# Booeb.com - Frontend Project Structure

Complete Next.js frontend application structure for the Booeb.com e-commerce marketplace.

## 📁 Directory Structure

```
frontend/
├── app/                              # Next.js App Router
│   ├── layout.tsx                   # Root layout
│   ├── page.tsx                     # Home page
│   ├── not-found.tsx                # 404 page
│   │
│   ├── (auth)/                      # Authentication routes
│   │   ├── layout.tsx
│   │   ├── login/page.tsx
│   │   ├── register/page.tsx
│   │   ├── forgot-password/page.tsx
│   │   ├── reset-password/page.tsx
│   │   └── verify-email/page.tsx
│   │
│   ├── (shop)/                      # Shopping routes
│   │   ├── layout.tsx
│   │   ├── products/page.tsx
│   │   ├── products/[id]/page.tsx
│   │   ├── category/[slug]/page.tsx
│   │   ├── search/page.tsx
│   │   ├── cart/page.tsx
│   │   ├── checkout/page.tsx
│   │   └── order-confirmation/page.tsx
│   │
│   ├── (account)/                   # User account routes
│   │   ├── layout.tsx
│   │   ├── dashboard/page.tsx
│   │   ├── orders/page.tsx
│   │   ├── orders/[id]/page.tsx
│   │   ├── wishlist/page.tsx
│   │   ├── profile/page.tsx
│   │   ├── addresses/page.tsx
│   │   └── settings/page.tsx
│   │
│   ├── (vendor)/                    # Vendor dashboard routes
│   │   ├── layout.tsx
│   │   ├── dashboard/page.tsx
│   │   ├── products/page.tsx
│   │   ├── products/new/page.tsx
│   │   ├── products/[id]/edit/page.tsx
│   │   ├── orders/page.tsx
│   │   ├── analytics/page.tsx
│   │   └── store-settings/page.tsx
│   │
│   ├── (admin)/                     # Admin panel routes
│   │   ├── layout.tsx
│   │   ├── dashboard/page.tsx
│   │   ├── products/page.tsx
│   │   ├── orders/page.tsx
│   │   ├── customers/page.tsx
│   │   ├── vendors/page.tsx
│   │   ├── categories/page.tsx
│   │   ├── coupons/page.tsx
│   │   ├── reports/page.tsx
│   │   └── settings/page.tsx
│   │
│   └── api/                         # API routes & webhooks
│       ├── auth/
│       ├── webhooks/
│       └── [...]
│
├── components/                       # React Components
│   ├── common/                      # Reusable components
│   │   ├── Header.tsx
│   │   ├── Footer.tsx
│   │   ├── Navigation.tsx
│   │   ├── Sidebar.tsx
│   │   ├── Button.tsx
│   │   ├── Card.tsx
│   │   ├── Modal.tsx
│   │   ├── Spinner.tsx
│   │   ├── Badge.tsx
│   │   ├── Alert.tsx
│   │   └── Pagination.tsx
│   │
│   ├── layout/                      # Layout components
│   │   ├── MainLayout.tsx
│   │   ├── AuthLayout.tsx
│   │   ├── AdminLayout.tsx
│   │   └── VendorLayout.tsx
│   │
│   ├── forms/                       # Form components
│   │   ├── LoginForm.tsx
│   │   ├── RegisterForm.tsx
│   │   ├── ProductForm.tsx
│   │   ├── CheckoutForm.tsx
│   │   ├── AddressForm.tsx
│   │   └── ProfileForm.tsx
│   │
│   ├── products/                    # Product-related components
│   │   ├── ProductCard.tsx
│   │   ├── ProductGrid.tsx
│   │   ├── ProductList.tsx
│   │   ├── ProductDetails.tsx
│   │   ├── ProductImages.tsx
│   │   ├── ProductReviews.tsx
│   │   ├── ProductRating.tsx
│   │   ├── RelatedProducts.tsx
│   │   └── ProductFilter.tsx
│   │
│   ├── cart/                        # Cart components
│   │   ├── CartItem.tsx
│   │   ├── CartSummary.tsx
│   │   ├── CartEmpty.tsx
│   │   └── MiniCart.tsx
│   │
│   ├── checkout/                    # Checkout components
│   │   ├── CheckoutSteps.tsx
│   │   ├── ShippingForm.tsx
│   │   ├── PaymentForm.tsx
│   │   ├── OrderReview.tsx
│   │   └── PaymentMethods.tsx
│   │
│   ├── account/                     # Account components
│   │   ├── Dashboard.tsx
│   │   ├── OrderHistory.tsx
│   │   ├── UserProfile.tsx
│   │   ├── AddressBook.tsx
│   │   └── WishlistSection.tsx
│   │
│   └── home/                        # Home page components
│       ├── HeroBanner.tsx
│       ├── TrustFeatures.tsx
│       ├── ShopByCategory.tsx
│       ├── FlashSales.tsx
│       ├── FeaturedProducts.tsx
│       ├── PromobannerSection.tsx
│       └── Newsletter.tsx
│
├── hooks/                            # Custom React Hooks
│   ├── useAuth.ts
│   ├── useCart.ts
│   ├── useWishlist.ts
│   ├── useProducts.ts
│   ├── useOrders.ts
│   ├── useFetch.ts
│   ├── useLocalStorage.ts
│   └── useDebounce.ts
│
├── context/                          # React Context
│   ├── AuthContext.tsx
│   ├── CartContext.tsx
│   ├── WishlistContext.tsx
│   ├── ThemeContext.tsx
│   ├── NotificationContext.tsx
│   └── FilterContext.tsx
│
├── lib/                              # Utility Libraries
│   ├── api.ts                       # API client setup
│   ├── auth.ts                      # Authentication utilities
│   ├── constants.ts                 # App constants
│   ├── types.ts                     # TypeScript types
│   ├── formatters.ts                # Data formatters
│   ├── validators.ts                # Form validators
│   ├── storage.ts                   # localStorage utilities
│   └── helpers.ts                   # General helpers
│
├── store/                            # Redux Store (if using Redux)
│   ├── index.ts
│   ├── slices/
│   │   ├── authSlice.ts
│   │   ├── cartSlice.ts
│   │   └── productSlice.ts
│   └── middleware/
│
├── styles/                           # Global Styles
│   ├── globals.css                  # Global styles
│   ├── variables.css                # CSS variables
│   ├── tailwind.config.js           # Tailwind config
│   └── fonts.css                    # Font declarations
│
├── public/                           # Static Assets
│   ├── images/
│   │   ├── logo/
│   │   ├── banners/
│   │   ├── products/
│   │   ├── icons/
│   │   └── placeholder.png
│   ├── fonts/
│   ├── icons/
│   ├── svg/
│   └── favicon.ico
│
├── .env.example                      # Environment variables template
├── .env.local                        # Local environment variables
├── next.config.js                    # Next.js configuration
├── tsconfig.json                     # TypeScript configuration
├── tailwind.config.js                # Tailwind CSS configuration
├── postcss.config.js                 # PostCSS configuration
├── jest.config.js                    # Jest configuration
├── package.json                      # Package dependencies
└── README.md                         # Frontend documentation
```

## 🎯 Key Features & Components

### Authentication (app/auth/)
- User registration with validation
- Email verification flow
- Social login integration
- Password reset functionality
- Session management

### Shopping (app/shop/)
- Product browsing with filters
- Advanced search functionality
- Category-based navigation
- Product comparison
- Add to cart
- Shopping cart management
- Checkout process
- Order confirmation

### User Account (app/account/)
- Dashboard overview
- Order history & tracking
- Wishlist management
- Address book
- Profile settings
- Account security

### Vendor Dashboard (app/vendor/)
- Store management
- Product inventory
- Order fulfillment
- Sales analytics
- Earnings tracking
- Store customization

### Admin Panel (app/admin/)
- Revenue analytics
- User management
- Order management
- Vendor moderation
- Product listings
- Category management
- Coupon management
- Reports & analytics

## 📦 Component Patterns

### Functional Component Example
```typescript
// components/products/ProductCard.tsx
import React from 'react';

interface ProductCardProps {
  id: string;
  name: string;
  price: number;
  image: string;
  rating: number;
}

export const ProductCard: React.FC<ProductCardProps> = ({
  id,
  name,
  price,
  image,
  rating
}) => {
  return (
    <div className="product-card">
      <img src={image} alt={name} />
      <h3>{name}</h3>
      <p>৳{price}</p>
      <div className="rating">⭐ {rating}</div>
    </div>
  );
};

export default ProductCard;
```

### Hook Example
```typescript
// hooks/useProducts.ts
import { useEffect, useState } from 'react';
import api from '@/lib/api';

export const useProducts = () => {
  const [products, setProducts] = useState([]);
  const [loading, setLoading] = useState(false);

  useEffect(() => {
    const fetchProducts = async () => {
      setLoading(true);
      try {
        const response = await api.get('/products');
        setProducts(response.data);
      } finally {
        setLoading(false);
      }
    };

    fetchProducts();
  }, []);

  return { products, loading };
};
```

## 🎨 Styling Convention

- **Framework**: Tailwind CSS
- **CSS Modules** for component-specific styles
- **CSS Variables** for theme customization
- **Mobile-first** approach
- **Responsive** at all breakpoints

## 🧪 Testing Structure

```
frontend/
├── __tests__/
│   ├── components/
│   ├── hooks/
│   ├── pages/
│   └── utils/
```

---

**Frontend Development is Ready!** 🚀
