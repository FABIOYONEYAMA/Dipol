- [API e Serviços](#api-e-serviços)
    -[Erro ao buscar geolocalização na API](#erro-ao-buscar-geolocalização-na-api)

<br>

## API e Serviços

Seção destinada a APIs e Serviços que automatizam fluxos de trabalhos, também descrevemos as **mensagens de erro que as APIs podem retornar**. Ela grava mensagens de erro e aviso no log dos **microserviços do backend**.


#### Erro ao buscar geolocalização na API



* **[error_message]** - _This IP, site or mobile application is not authorized to use this API key. Request received from IP address_

_**O registro de logs do backend informam** que o endereço ip registrado no log não está autorizado a usar a chave API para esta solicitação._ Para solucionar o problema é necesário realizar o procedimento abaixo:

Acesse o log do backend **[dipol-endereco-service]:**

```bash
kubectl logs -l app=dipol-endereco-service -f

```
![Erro_not_authorized_api_key](/assets/img/erro-ao-buscar-geolocalização-na-api_001.png)

**Salve os endereços** que apresentam erro na mensagem e adicione na **Whitelist da API MAPS**.
