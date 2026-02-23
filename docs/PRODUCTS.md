# Product Management Guide

## Product Model

The `Product` model is the core of the BabyHappy catalog:

```python
class Product(models.Model):
    name = models.CharField(max_length=255)
    slug = models.SlugField(unique=True)
    description = models.TextField()
    price = models.DecimalField(max_digits=10, decimal_places=2)
    category = models.ForeignKey(Category, on_delete=models.CASCADE)
    image = models.ImageField(upload_to='products/')
    stock = models.PositiveIntegerField(default=0)
    is_active = models.BooleanField(default=True)
    created_at = models.DateTimeField(auto_now_add=True)
```

## Categories

Baby products are organized into categories:
- 🍼 Feeding
- 🛏️ Sleep
- 🧸 Toys
- 🚿 Bath & Care
- 👶 Clothing
- 🚗 Travel

## Adding Products via Admin

1. Go to `/admin/`
2. Click "Products" → "Add Product"
3. Fill in all required fields
4. Upload product image
5. Set stock quantity
6. Click "Save"

## Product Images

Images are uploaded to the `MEDIA_ROOT/products/` directory.

In production, configure `AWS_STORAGE_BUCKET_NAME` to use S3 instead.

## Inventory Management

When stock reaches 0, the product shows as "Out of Stock" and cannot be added to cart.

Low stock alerts can be configured in `apps/inventory/config.py`.
