# 🍓 FruitBasket

FruitBasket är en enkel, serverlös webbtjänst byggd med AWS-tjänster som låter användare lägga till frukter till en DynamoDB-tabell via ett REST API. Projektet syftar till att demonstrera hur man kan bygga en cloud-native applikation med hjälp av AWS Lambda, API Gateway och DynamoDB – helt definierat med en CloudFormation-template.

## 🚀 Funktionalitet

- Lägg till frukter (med `id`, `name`, och `color`) via ett POST-anrop.
- All data sparas i en DynamoDB-tabell.
- Serverlös arkitektur för hög tillgänglighet och skalbarhet.

## 🧱 Arkitektur

Projektet använder sig av följande AWS-resurser:

- **DynamoDB**: För lagring av fruktdata.
- **Lambda**: Kör affärslogik för att ta emot och spara inkommande data.
- **API Gateway**: Skapar ett REST API och kopplar det till Lambda-funktionen.
- **IAM**: Ger Lambda rättigheter att skriva till DynamoDB.
- **CloudFormation**: Automatiserar hela infrastrukturen som kod.

```plaintext
Client
  │
  └──> API Gateway ──> Lambda Function ──> DynamoDB Table
