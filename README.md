# Next.js E-commerce Application

[Next JS E-commerce Application](https://www.youtube.com/watch?v=5miHyP6lExg)

---
## Admin Dashboard
> ecommerce_admin
``` bash
npx create-next-app@latest ecommerce-admin --typescript --tailwind --eslint
```

### Tools & Components

1. [Shadcn UI library](https://ui.shadcn.com/docs)
    ``` bash
    npx shadcn-ui@latest add form
    npx shadcn-ui@latest add input
    ```

2. [Clerk Authentication](https://clerk.com/)

3. [Prisma DB-ORM](https://www.prisma.io/)
    ``` bash
    npm i -D prisma
    npm i @prisma/client
    npx prisma init
    ....
    npx prisma generate                 # for intellisense
    npx prisma db push

    npx prisma migrate reset            # how to reset db
    npx prisma generate
    npx prisma db push
    ```

4. [Cloudinary](https://cloudinary.com/) -> Image hosting

>.env 
``` 
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY= **********
CLERK_SECRET_KEY= **********
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/

DATABASE_URL= **********
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME= **********
STRIPE_API_KEY= **********
FRONTEND_STORE_URL="http://localhost:3001" (URL of the ecommerce-store)
STRIPE_WEBHOOK_SECRET= **********
```

---
## Store
> ecommerce_store
``` bash
npx create-next-app@latest ecommerce-store --typescript --tailwind --eslint
```

1. [Lucide React](https://lucide.dev/)
    ``` bash
    npm i lucide-react
    ```
2. [Headless UI library](https://headlessui.com/)
    ``` bash
    npm i @headlessui/react
    ```
3. [Recharts](https://recharts.org/en-US/) -> Sales Dashboard
    ``` bash
    npm i recharts
    ```
>.env  
``` 
NEXT_PUBLIC_API_URL=http://localhost:3000/api/(storeId)
```
>>> Its provided in the ecommerce-admin, can be found from there

---
### Nice npm packages (extra)
>query-string

---
### Trics
1. To avoid hydration errors
``` javascript
    const [isMounted, setIsMounted] = useState(false);

    useEffect(() => {
        setIsMounted(true);
    }, []);

    if (!isMounted) {
        return null;
    }
```