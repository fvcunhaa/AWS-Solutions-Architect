# AWS Compute Optimizer – Otimização de Recursos e Custos

## Visão Geral

O **AWS Compute Optimizer** é um serviço da Amazon Web Services que analisa métricas históricas de utilização para recomendar configurações ideais de recursos computacionais.

Ele utiliza dados do Amazon CloudWatch e algoritmos de machine learning para identificar recursos superdimensionados ou subdimensionados, ajudando a melhorar desempenho e reduzir custos.

O serviço fornece recomendações para:

- Amazon EC2
- Amazon RDS
- Auto Scaling Groups
- AWS Lambda
- Amazon EBS

O objetivo é garantir que os recursos estejam corretamente dimensionados conforme o padrão real de uso da aplicação.



## Contexto Arquitetural

Considerando uma arquitetura típica em VPC com:

<img width="857" height="439" alt="image" src="https://github.com/user-attachments/assets/d7472917-9eef-40de-bc3f-01b0145ab2b9" />


- Subnets privadas e públicas
- Instâncias EC2
- Amazon RDS (Primary e Read Replica)
- NAT Gateway
- Amazon S3 para backup
- Múltiplas Availability Zones

O Compute Optimizer analisa principalmente:

- Utilização de CPU
- Memória (quando habilitado via agente)
- Throughput de rede
- IOPS de disco
- Padrões de workload

Com base nesses dados, ele sugere:

- Redimensionamento de instâncias EC2
- Ajuste de classe de instâncias RDS
- Alteração de tipo/volume EBS
- Ajustes em Auto Scaling Groups



## Como Funciona

1. Métricas são coletadas via CloudWatch.
2. O Compute Optimizer analisa o histórico (normalmente 14 dias ou mais).
3. Modelos preditivos avaliam eficiência.
4. Recomendações são exibidas no console AWS.
5. O usuário pode aplicar a recomendação manualmente ou automatizar o processo.



## Tipos de Recomendações

- **Overprovisioned**: recurso superdimensionado
- **Underprovisioned**: recurso insuficiente
- **Optimized**: recurso corretamente dimensionado

Cada recomendação apresenta:

- Nível de confiança
- Economia estimada
- Impacto esperado em performance



## Casos de Uso

- Redução de custos em ambientes produtivos
- Ajuste fino de instâncias RDS e EC2
- Otimização contínua de workloads
- Governança financeira (FinOps)
- Revisão periódica de capacidade



## Integração com Outros Serviços

O Compute Optimizer utiliza dados de:

- Amazon CloudWatch
- AWS Cost Explorer
- AWS Organizations (ambientes multi-conta)
- AWS Trusted Advisor

Pode ser integrado com:

- Processos FinOps
- Pipelines de automação
- Estratégias de re-architecture para cloud-native



## Boas Práticas

- Habilitar métricas detalhadas no CloudWatch
- Ativar coleta de memória para EC2
- Revisar recomendações periodicamente
- Testar mudanças antes de aplicar em produção
- Integrar recomendações ao processo de governança de custos



## Limitações

- Baseado em histórico de utilização (não prevê eventos atípicos futuros)
- Não aplica mudanças automaticamente
- Recomendações dependem da qualidade das métricas
- Pode não considerar particularidades específicas de workload



## Conclusão

O AWS Compute Optimizer é uma ferramenta estratégica para otimização de custos e eficiência operacional em ambientes AWS.

Ao analisar padrões reais de uso, ele fornece recomendações baseadas em dados, permitindo decisões informadas sobre redimensionamento de recursos.

Em arquiteturas multi-AZ com EC2 e RDS, seu uso contínuo contribui para:

- Melhor alocação de recursos
- Redução de desperdício
- Aumento de eficiência financeira
- Evolução para uma arquitetura mais cloud-native
