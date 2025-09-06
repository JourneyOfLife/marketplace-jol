# Journey Of Life (JOL) Marketplace

[![Django Version](https://img.shields.io/badge/Django-5.0-green)](https://www.djangoproject.com/)
[![Python Version](https://img.shields.io/badge/Python-3.12-blue)](https://www.python.org/)
[![AGPLv3 License](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](LICENSE)
[![Code Style: Black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

A scalable, open-source marketplace platform connecting manufacturers and distributors of ecclesiastical goods with churches across the European Union. Built with Django, Docker, and modern web technologies.

## 🚀 Vision

To become the primary digital infrastructure for the ecclesiastical supply chain in Europe, simplifying procurement for over 400,000 churches while providing sellers with a pan-European storefront.

## 📋 High-Level Architecture

The system is designed as a collection of loosely coupled services orchestrated by Docker and Kubernetes.

```mermaid
graph TB
    subgraph "JOL Platform"
        WEB[Web Frontend<br>React]
        GATEWAY[API Gateway<br>Nginx]
        AUTH[Auth Service]
        MS1[Products Service<br>Django]
        MS2[Orders Service<br>Django]
        MS3[Search Service<br>Django]
        ES[Elasticsearch]
        DB[PostgreSQL]
        CACHE[Redis]
        AI[AI Integration Layer]
    end

    WEB --> GATEWAY
    GATEWAY --> AUTH
    GATEWAY --> MS1
    GATEWAY --> MS2
    GATEWAY --> MS3
    MS1 --> DB
    MS2 --> DB
    MS3 --> ES
    MS1 --> CACHE
    AUTH --> CACHE
    MS3 --> AI
