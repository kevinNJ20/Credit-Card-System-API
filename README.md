# Credit Card System API

API System qui expose les opérations sur les cartes de crédit via Supabase.

## Description

Cette API fournit un accès standardisé aux cartes de crédit. Elle suit le pattern API-Led Connectivity comme System API.

## Endpoints

### GET /api/creditcards/cards
Récupère la liste des cartes avec filtres.

**Query Parameters:**
- `customerId` (optional): ID du client propriétaire
- `cardNumber` (optional): Numéro de carte
- `status` (optional): Statut de la carte
- `limit` (optional, default: 100)
- `offset` (optional, default: 0)

### POST /api/creditcards/cards
Crée une nouvelle carte de crédit.

### GET /api/creditcards/cards/{cardId}
Récupère une carte par son ID.

### PUT /api/creditcards/cards/{cardId}
Met à jour une carte (inclut les contrôles et limites).

## Configuration

Voir README.md de Core Banking Customers System API pour la configuration de base.

### Tables Utilisées

- `cards`: Table principale des cartes de crédit

## Architecture Technique

### Flows Business-Logic

- `get-cards-business-logic`: Liste des cartes
- `create-card-business-logic`: Création de carte
- `get-card-by-id-business-logic`: Récupération par ID
- `update-card-business-logic`: Mise à jour (contrôles inclus)

## Exemples de Requêtes

### POST /api/creditcards/cards

```bash
curl -X POST http://localhost:8081/api/creditcards/cards \
  -H "Content-Type: application/json" \
  -d '{
    "cardNumber": "4111111111111111",
    "cardType": "Credit",
    "cardNetwork": "Visa",
    "customerId": "123e4567-e89b-12d3-a456-426614174000",
    "cardholderName": "John Doe",
    "expirationDate": "2025-12-31",
    "status": "Active",
    "creditLimit": 5000.00,
    "controls": {
      "dailyPurchaseLimit": 1000.00,
      "internationalTransactionsEnabled": true,
      "onlineTransactionsEnabled": true
    }
  }'
```

