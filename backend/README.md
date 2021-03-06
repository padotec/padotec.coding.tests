#  Desafio para pessoa desenvolvedora back-end junior

---     

## Criação da API de cadastro de dispositivos

**Descrição:** A Empresa XYZ deseja desenvolver um sistema para cadastro de seus dispositivos IoT, dessa forma, você como desenvolvedor back-end deverá desenvolver as API's necessárias.

```
Requisitos técnicos:

Linguagem: Java 11
Framework: Spring / Spring Boot
Database: H2 in memory
Mensageria: RabbitMQ
Git: Para cada desafio a seguir (1, 2, 3, 4, 5, 6), deve ser criado uma branch com os commits da funcionalidade, 
realize os merges com a branch principal mas não delete as branches criadas ao decorrer dos desafios.
```

---
### As seguintes funcionalidades deverão ser desenvolvidas:

1. **Cadastro de um único dispositivo IoT**: Cadastro simples de dispositivo

```json
Request URI: "/registrar";
Verbo: POST
Body: Json
{
  "name": "nome do dispositivo",
  "mac": "mac do dispositivo",
  "email": "email do dono do dispositivo",
  "latitude": "latitude",
  "longitude": "longitude"
}

Response: 201
{
  "deviceId": "id do dispositivo (gerado no back-end)",
  "mac": "mac do dispositivo"
}

```
---
2. **Listar todos os dispositivos cadastrados**: Todos os dispositivos são retornados em uma lista de objetos
```json
Request URI: "/listar"
Verbo: GET

Response: 200
[
  {
    "deviceId": "id do dispositivo 1 (gerado no back-end)",
    "name": "nome do dispositivo 1",
    "mac": "mac do dispositivo 1",
    "email": "email do dono do dispositivo 1",
    "latitude": "latitude 1",
    "longitude": "longitude 1",
  },
  {
    "deviceId": "id do dispositivo 2 (gerado no back-end)",
    "name": "nome do dispositivo 2",
    "mac": "mac do dispositivo 2",
    "email": "email do dono do dispositivo 2",
    "latitude": "latitude 2",
    "longitude": "longitude 2"
  },
  ...

]
```
---
3. **Listar dispositivo pelo "deviceId"**: O usuário irá informar o id do dispositivo que ele deseja consultar na URI
```json
Request URI: "/listar/deviceId" //e.g. -> /listar/1
Verbo: GET

Response: 200
{
  "deviceId": "id do dispositivo 1 (gerado no back-end)",
  "name": "nome do dispositivo 1",
  "mac": "mac do dispositivo 1",
  "email": "email do dono do dispositivo 1",
  "latitude": "latitude 1",
  "longitude": "longitude 1",
}
```
---

4. Cadastro de vários dispositivos IoT: Poderá ser enviado uma lista com diversos dispositivos para cadastro de uma única só vez, para isso esses cadastros deverão ser processados de forma assíncrona. Dessa forma esse endpoint confirma imediatamente que a requisição foi aceita (STATUS 202) enviando os dados para uma fila (Queue) do RabbitMQ. Implementar também um "Listener" que deve escutar essa fila (Queue) e processar o cadastro dos dispositivos.

```json
Request URI: "/registrar/async";
Verbo: POST
Body: Json
[
  {
    "name": "nome do dispositivo 1",
    "mac": "mac do dispositivo 1",
    "email": "email do dono do dispositivo 1",
    "latitude": "latitude 1",
    "longitude": "longitude 1",
  },
  {
    "name": "nome do dispositivo 2",
    "mac": "mac do dispositivo 2",
    "email": "email do dono do dispositivo 2",
    "latitude": "latitude 2",
    "longitude": "longitude 2"
  },
  ...

]

Response: 202
```
---
5. Criar uma Dockerfile para a aplicação desenvolvida.  
6. Descrever as instruções para executar a aplicação preferencialmente no README.md  
7. Disponibilizar a aplicação em seu Github informando a url para acesso.  
---

Boa sorte! =}
