# Maybe (Fork): The Personal Finance App for Everyone

> \[!IMPORTANT]
> This repository is a **fork** of the original project
> [maybe-finance/maybe](https://github.com/maybe-finance/maybe),
> which is no longer maintained.
> My fork ensures the project remains usable.
> ⚠️ Please note: This project is **not affiliated with Maybe Finance Inc.**

---

## Hosting

This forked version of Maybe is a fully functional finance app that can be
easily [self-hosted via Docker](docs/hosting/docker.md).

### 🚀 Quickstart with Docker Compose

Create a `docker-compose.yml` file in your project folder with the following content:

```yaml
version: "3.9"

services:
  db:
    image: postgres:15-alpine
    restart: always
    environment:
      POSTGRES_USER: maybe
      POSTGRES_PASSWORD: maybe
      POSTGRES_DB: maybe_production
    volumes:
      - db_data:/var/lib/postgresql/data

  web:
    build: .
    restart: always
    depends_on:
      - db
    ports:
      - "3000:3000"
    environment:
      DATABASE_URL: postgres://maybe:maybe@db:5432/maybe_production
      RAILS_ENV: production
    command: bash -c "bin/setup && bin/dev"

volumes:
  db_data:
```

Then start the application with:

```bash
docker-compose up -d
```

👉 The app will then be available at:
[**http://localhost:3000**](http://localhost:3000) or [**http://SERVER-IP:3000**](http://SERVER-IP:3000)

---

## Origin & Attribution

The original project was published by **Maybe Finance Inc.** under AGPLv3.
Since it is no longer maintained, this repository is based on it — with the necessary adjustments.

Important points:

* The original license remains in place:
  [AGPLv3 License](https://github.com/TillitschScHocK/maybe/blob/main/LICENSE)
* If you create forks, please state that your project is based on Maybe Finance but is **not affiliated with or endorsed by** them.
* The name **"Maybe"** as well as the official logo are trademarks of Maybe Finance Inc.
  → Use in forks is not permitted.

---

## License & Copyright

This project is based on Maybe Finance and remains under the
[AGPLv3 License](https://github.com/TillitschScHocK/maybe/blob/main/LICENSE).

⚠️ Note:
**"Maybe" is a registered trademark of Maybe Finance Inc.**
This fork repository is **not** affiliated with Maybe Finance Inc.
