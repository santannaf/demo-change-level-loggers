# Documentação do Spring Actuator e Loggers

## Introdução

O **Spring Actuator** é uma ferramenta poderosa que fornece funcionalidades adicionais para aplicações Spring Boot. Ele permite a gestão e monitoramento da aplicação em tempo real, facilitando a identificação e resolução de problemas.

## Recursos do Spring Actuator

Um dos recursos-chave do Actuator é a capacidade de alterar o nível de log da aplicação através de endpoints REST, sem necessidade de reiniciar a aplicação. Isso permite ajustes finos no monitoramento da aplicação, especialmente em ambientes de produção.

## Alterando Níveis de Log com Spring Actuator

Para alterar dinamicamente os níveis de log, você pode utilizar os seguintes endpoints do Actuator:

1. **Consultar o nível de log atual (GET)**:
    - **Endpoint**: `GET /actuator/loggers`
    - **Descrição**: Retorna um mapeamento de todos os loggers e seus níveis de log correspondentes.

2. **Alterar o nível de log (POST)**:
    - **Endpoint**: `POST /actuator/loggers/{logger-name}`
    - **Corpo da solicitação**:
      ```json
      {
        "configuredLevel": "DEBUG"
      }
      ```
    - **Descrição**: Altera o nível de log do logger especificado, substituindo `{logger-name}` pelo nome do logger desejado (ex: `com.seu.pacote`).

## Utilização Correta dos Níveis de Log

A utilização correta dos níveis de log – **TRACE**, **DEBUG**, **INFO**, **WARN** e **ERROR** – é fundamental para garantir a eficiência na coleta de dados de telemetria e observabilidade:

- **TRACE**: Detalhes para rastreamento; uso recomendado durante desenvolvimento.
- **DEBUG**: Mensagens úteis para depuração; evite em produção devido ao volume gerado.
- **INFO**: Mensagens gerais sobre o estado da aplicação; relatam eventos normais.
- **WARN**: Indicam situações inesperadas que requerem atenção, mas não impactam criticamente.
- **ERROR**: Registra falhas graves que afetam a operação da aplicação.

## Regra de Ouro para Uso de Logs

- **TRACE**: Use durante o desenvolvimento e testes.
- **DEBUG**: Utilize em situações específicas; evite em produção.
- **INFO**: Relate eventos relevantes em funcionamento normal.
- **WARN**: Indique comportamentos inesperados que não são críticos.
- **ERROR**: Registre falhas que requerem atenção imediata.

## Exemplo Prático de Uso

### Sistema de Pedidos Online

- **TRACE**: Iniciar um pedido, registrando cada passo (ex: "validando endereço").
- **DEBUG**: Processar um pagamento, registrando detalhes em caso de erro.
- **INFO**: Confirmar um pedido, registrando "Pedido 12345 confirmado com sucesso".
- **WARN**: Cliente tenta usar um código de cupom inválido, registrando "Cliente tentou usar código de desconto inválido".
- **ERROR**: Falha na transação, registrando "Erro na transação do pedido 12345: Details do erro".

## Considerações Finais

A gestão eficaz dos níveis de log é essencial para manter a saúde da aplicação e a capacidade de resposta em produção. O Spring Actuator permite ajustar esses níveis dinamicamente, otimizando custos e aumentando a eficiência na resolução de problemas.
