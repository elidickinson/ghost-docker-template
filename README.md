# Ghost Development / Simple Hosting Docker Template

Quickly get running with Ghost in a single docker container using an SQlite database. Suitable for local development or production hosting if the traffic volume isn't too high.

## Quick Start

```bash
cp .env.example .env  # Configure mail settings
docker-compose up -d
```

Access at `http://localhost:2368` (admin: `/ghost`)

## Configuration

### Mailgun set up

1. Sign up at [Mailgun](https://www.mailgun.com/)
2. Create and verify a domain
3. Get SMTP credentials: Dashboard → Domain Settings → SMTP credentials
4. Add to `.env`:
   ```env
   MAIL_FROM=your-email@your-domain.com
   MAIL_HOST=smtp.mailgun.org
   MAIL_PORT=587
   MAIL_USER=postmaster@your-domain.mailgun.org
   MAIL_PASSWORD=your-smtp-password
   ```
5. For newsletters: Copy your Mailgun API key and add it in Ghost admin → Settings → Email newsletter → Mailgun API key

### Additional Options

Modify `docker-compose.yml` environment variables for admin URL, privacy, security, logging, etc.

## Commands

```bash
docker-compose up -d          # Start
docker-compose down           # Stop
docker-compose logs -f ghost  # View logs
rm -rf ghost-data/*           # Delete database and site data (!)
```

## Structure

- `docker-compose.yml` - Docker config
- `.env` - Environment variables
- `ghost-data/` - Persistent storage for site data
