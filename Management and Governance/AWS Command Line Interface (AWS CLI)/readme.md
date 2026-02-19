# AWS CLI (Command Line Interface)

## Visão Geral

O **AWS CLI (Command Line Interface)** é a ferramenta oficial da Amazon Web Services para gerenciamento de serviços AWS via linha de comando.

Ele permite interagir com praticamente todos os serviços AWS diretamente pelo terminal, enviando requisições para as APIs da AWS de forma automatizada e padronizada.

É amplamente utilizado para:

- Automação de tarefas
- Administração de infraestrutura
- Execução de comandos operacionais
- Integração com pipelines DevOps
- Gestão de múltiplos ambientes

Funciona em Windows, macOS e Linux, podendo ser utilizado localmente ou em servidores e instâncias EC2.



## Como Funciona

O AWS CLI atua como um cliente que:

1. Recebe um comando no terminal.
2. Utiliza credenciais configuradas localmente.
3. Envia uma requisição HTTPS para a API do serviço AWS.
4. Retorna a resposta no formato escolhido (JSON, table ou text).

Estrutura básica de comando:

aws <serviço> <operação> [parâmetros]

aws ec2 describe-instances

aws s3 ls

aws rds describe-db-instances

## Configuração Inicial

Após a instalação, execute:
aws configure

Informe:

- AWS Access Key ID
- AWS Secret Access Key
- Região padrão
- Formato de saída

As configurações são armazenadas em:

~/.aws/credentials

~/.aws/config




## Principais Recursos

- Gerenciamento completo de serviços AWS
- Suporte a múltiplos perfis (dev, staging, prod)
- Integração com scripts e automação
- Suporte a IAM Roles e credenciais temporárias
- Saída formatada em JSON, table ou text



## Casos de Uso

- Provisionamento de recursos
- Deploy automatizado
- Criação de backups
- Auditoria e inventário de infraestrutura
- Integração com CI/CD
- Operação NOC / SRE



## Boas Práticas

- Preferir IAM Roles ou credenciais temporárias
- Separar perfis por ambiente
- Utilizar filtros e queries para reduzir saída
- Versionar scripts que utilizam CLI
- Manter a ferramenta atualizada



## Limitações

- Requer permissões IAM adequadas
- Depende de conectividade com AWS
- Não substitui SDKs para lógica complexa
- Respostas extensas podem exigir processamento adicional



## Conclusão

O AWS CLI é uma ferramenta essencial para administração e automação de ambientes AWS.  
Ele oferece controle direto, integração com automação e capacidade de escalar operações de forma eficiente e programática.

