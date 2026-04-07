# Finance - Personal Finance Dashboard

A modern personal finance management app built with Next.js, Prisma, and Clerk for authentication.

## What is this?

Welth helps you track your spending across multiple accounts, set budgets, and get insights into your financial habits. It's designed to be simple but powerful—no bloat, just what you need to manage your money.

## Features

- **Multiple Accounts** - Manage checking, savings, credit cards, all in one place
- **Transaction Tracking** - Log transactions with categories and notes
- **Budget Management** - Set monthly budgets and track spending against them
- **Receipt Scanning** - Upload receipts for automatic transaction capture (coming soon)
- **Dark Mode** - Because who doesn't use dark mode?
- **Real-time Updates** - See your finances update instantly

## Tech Stack

- **Frontend** - Next.js 15 with React 18
- **Database** - PostgreSQL via Supabase
- **ORM** - Prisma
- **Auth** - Clerk
- **Styling** - Tailwind CSS
- **UI Components** - Radix UI
- **Email** - Resend

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn
- A Supabase account (free tier works fine)
- A Clerk account (free tier works fine)

### Installation

1. Clone the repo and install dependencies:
```bash
git clone <repo-url>
cd finance
npm install
```

2. Set up environment variables in `.env.local`:
```
DATABASE_URL=your_supabase_pooling_connection
DIRECT_URL=your_supabase_direct_connection
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_key
CLERK_SECRET_KEY=your_clerk_secret
```

Get these from:
- **Supabase**: Create a project, go to Settings → Database → Connection strings
- **Clerk**: Go to dashboard.clerk.com → API Keys

3. Push the database schema:
```bash
npx prisma db push
```

4. Start the dev server:
```bash
npm run dev
```

Open http://localhost:3000 and sign up!

## Project Structure

```
├── app/                    # Next.js app directory
│   ├── (auth)/            # Auth pages (sign-in, sign-up)
│   ├── (main)/            # Protected app pages
│   │   ├── dashboard/
│   │   ├── account/
│   │   └── transaction/
│   └── api/               # API routes
├── components/            # Reusable React components
│   ├── ui/               # UI component library
│   └── _components/      # Feature-specific components
├── actions/              # Server actions
├── lib/                  # Utilities
├── prisma/              # Database schema
└── hooks/               # Custom React hooks
```

## Database Schema

The app tracks:
- **Users** - Synced with Clerk
- **Accounts** - Checking, savings, credit cards, etc.
- **Transactions** - Individual money movements
- **Budgets** - Monthly spending limits

## Development

### Run migrations
```bash
npx prisma migrate dev
```

### Generate Prisma client after schema changes
```bash
npx prisma generate
```

### View database with Prisma Studio
```bash
npx prisma studio
```

## Deployment

The app is ready to deploy on Vercel:

```bash
git push origin main
# Deploy from Vercel dashboard
```

Just make sure your environment variables are set in Vercel project settings.

## Common Issues

**Can't connect to database?**
- Check your Supabase project isn't paused
- Verify DATABASE_URL and DIRECT_URL are correct
- Make sure the password includes special characters correctly

**Auth not working?**
- Verify Clerk keys are correct
- Check NEXT_PUBLIC_CLERK_SIGN_IN_URL and related URLs in env

**Build errors?**
- Clear .next directory: `rm -r .next`
- Regenerate Prisma client: `npx prisma generate`

## License

MIT - do whatever you want with it

## Contributing

Found a bug or have a feature idea? Feel free to open an issue or PR.

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
