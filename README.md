# SGS OpenMRS 3.0 Application

A containerized deployment of OpenMRS 3.0 with custom configurations for the SGS healthcare system.

## 🌐 Overview

This repository contains the build configuration for the SGS OpenMRS 3.0 application, deployed at [sgs.uwdigi.org](http://sgs.uwdigi.org/).

## 🚀 Quick Start

### Prerequisites

- Docker and Docker Compose
- Git
- Access to SMS API credentials
- OpenMRS user credentials

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-org/sgs-o3
   cd sgs-o3
   ```

2. Set up environment variables:
   ```bash
   cp .env.example .env
   ```

3. Configure the following in `.env`:
   - SMS API credentials (USERNAME and API KEY)
   - OpenMRS user credentials
   - OpenMRS Questionnaire API endpoint URL
   - Outcomes endpoint URL

4. Download and configure domain certs:
   ```bash
   docker compose -f docker-compose-init.yml up
   ```

5. Stop the Nginx server after certs are downloaded:
   ```bash
   docker compose -f docker-compose-init.yml down
   ```
   
4. Start the application:
   ```bash
   docker compose up
   ```
## 💾 Database Management

### Backup and Restore

To restore from a backup:

1. Place your SQL backup file in the `db` folder
2. Update the following configurations in `.env`:
   ```env
   OMRS_CONFIG_AUTO_UPDATE_DATABASE=false
   OMRS_CONFIG_CREATE_TABLES=false
   ```
3. Restart the application:
   ```bash
   docker compose down
   docker compose up
   ```

### Creating a Backup

```bash
docker exec sgs-mariadb mysqldump -u$MYSQL_USER -p$MYSQL_PASSWORD openmrs > backup_$(date +%Y%m%d).sql
```

## 🧹 Cleanup

To completely remove the application and its volumes:

```bash
docker compose down -v
```

## 🔧 Configuration

Key configuration files:
- `docker-compose.yml`: Container orchestration
- `.env`: Environment variables
- `db/`: Database initialization scripts

## 🛟 Troubleshooting

Common issues and solutions:

1. Database connection errors:
   - Verify MariaDB container is running
   - Ensure proper network connectivity

2. SMS API issues:
   - Validate API credentials
   - Check network connectivity to SMS service
   - Review API endpoint configuration

## 📚 Additional Resources

- [OpenMRS Documentation](https://wiki.openmrs.org/)
- [Docker Documentation](https://docs.docker.com/)
- [MariaDB Documentation](https://mariadb.org/documentation/)

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request
