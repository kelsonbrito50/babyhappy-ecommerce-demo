# API Reference

## Base URL

```
http://localhost:8000/
```

## Authentication

Session-based authentication. Login via `/accounts/login/`.

## Endpoints

### Products

#### `GET /products/`
Returns paginated list of available products.

#### `GET /products/<slug>/`
Returns details for a specific product.

### Cart

#### `POST /cart/add/`
Adds an item to the shopping cart.

**Body (form data):**
- `product_id` — Product ID
- `quantity` — Quantity (default: 1)

#### `GET /cart/`
Returns current cart contents.

#### `POST /cart/remove/<item_id>/`
Removes item from cart.

### Checkout

#### `POST /checkout/`
Processes checkout and initiates payment.

**Body:**
- `shipping_address` — Delivery address
- `payment_method` — `credit_card`

### Orders

#### `GET /orders/`
Returns user's order history.

#### `GET /orders/<id>/`
Returns order details and status.

## Payment Integration

Payment is processed via Cielo. See Cielo documentation for transaction statuses.

## Error Handling

All errors return appropriate HTTP status codes with a JSON body:
```json
{"error": "Description of the error"}
```
