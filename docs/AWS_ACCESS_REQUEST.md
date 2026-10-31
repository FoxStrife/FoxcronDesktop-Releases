# Acesso AWS e recursos monitorados

O Foxcron usa a conta nominal do operador no **AWS IAM Identity Center**, com credenciais temporárias obtidas por SSO. Não exige cadastrar Access Key/Secret Key permanentes nem colar chaves temporárias em tela.

O portal e a região SSO são configurados em **Meu acesso**. A região do Identity Center pode ser diferente da região de um recurso; não altere esse valor para corrigir um erro sem confirmar com o responsável pela conta. Os recursos monitorados desta versão estão em `us-east-1`.

## Escopo da versão 1.23.0

- Função operacional: `SupportUserNOC`, na conta Pricefy configurada no aplicativo.
- Logs: `/ecs/automacao-ofertas-futuras-paguemenos`.
- RDS: `prod-paguemenos-integracao-db`, métrica CPUUtilization do CloudWatch.
- Cinco filas SQS fixas:
  1. `sqs-arquivo-integracao-pague-menos-prd.fifo`
  2. `sqs-arquivo-integracao-dlq-pague-menos-prd.fifo`
  3. `sqs-persistencia-precos-pague-menos-prd`
  4. `sqs-persistencia-precos-dlq-pague-menos-prd`
  5. `sqs-recebimento-campanhas-dlq-pague-menos-prd`

Conta, função e recursos são específicos deste ambiente. Incluir novas filas ou outro ambiente requer atualização do aplicativo, não apenas cadastro de outra URL.

## Permissões de consulta

| Operação | Finalidade |
| --- | --- |
| `logs:DescribeLogStreams` | Localizar o stream do dia no grupo configurado |
| `logs:FilterLogEvents` | Ler os eventos filtrados de ofertas futuras |
| `cloudwatch:GetMetricStatistics` | Consultar a estatística CPUUtilization |
| `sqs:GetQueueAttributes` | Obter ApproximateNumberOfMessages nas filas configuradas |

O Foxcron confirma a conta com `sts:GetCallerIdentity` antes das consultas. A operação não exige concessão explícita de permissão e não comprova acesso aos demais serviços. A identidade também precisa estar habilitada a obter a função da conta pelo SSO.

Não é necessário acesso SQL ao RDS. Não são solicitadas operações de envio, recebimento, limpeza ou exclusão de mensagens SQS. As consultas não autorizam o aplicativo a modificar políticas AWS.

## Modelo para o administrador

[aws-readonly-policy.example.json](aws-readonly-policy.example.json) é um exemplo para revisão pelo administrador, não uma política aplicada pelo aplicativo. Substitua a conta fictícia `123456789012`, confira os recursos e a região, e considere as políticas efetivas da organização e do permission set SSO.

`cloudwatch:GetMetricStatistics` usa `Resource: "*"` com condição de região no exemplo; não limita a leitura a uma única instância RDS por ARN. `FilterLogEvents` autoriza leitura no grupo, não apenas a frase usada pelo aplicativo. `GetQueueAttributes` pode autorizar outros atributos das filas, embora o Foxcron peça somente a contagem disponível.

## Referências

- [AWS: ações de SQS](https://docs.aws.amazon.com/service-authorization/latest/reference/list_sqs.html).
- [AWS: GetQueueAttributes e contagens aproximadas](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_GetQueueAttributes.html).
- [AWS: ações de CloudWatch](https://docs.aws.amazon.com/service-authorization/latest/reference/list_cloudwatch.html).
- [AWS: ações de CloudWatch Logs](https://docs.aws.amazon.com/service-authorization/latest/reference/list_logs.html).
- [AWS: GetCallerIdentity](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetCallerIdentity.html).
