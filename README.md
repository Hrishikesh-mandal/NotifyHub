# Event-Driven Notification System

A scalable, fault-tolerant notification system built with microservices architecture using Kafka, Redis, and PostgreSQL. This system handles multi-channel notifications (Email & SMS) with features like idempotency, rate limiting, retry mechanisms, and dead-letter queues.

## 🎯 Overview

This Event-Driven Notification System is designed to handle high-volume notification processing across multiple channels. It leverages Apache Kafka for event streaming, Redis for caching and rate limiting, and PostgreSQL for persistent storage. The system ensures reliable message delivery with retry mechanisms and dead-letter queue handling.

### Key Capabilities

- **Multi-Channel Support**: Email and SMS notifications
- **Event-Driven Architecture**: Kafka-based message streaming
- **Idempotency**: Prevents duplicate notification processing
- **Rate Limiting**: Controls notification frequency per user
- **Retry Mechanism**: Automatic retry with exponential backoff
- **Dead-Letter Queue**: Handles failed messages for manual intervention
- **Database Persistence**: Tracks notification status and history
- **Monitoring**: Integrated with Kafdrop for Kafka monitoring

## ✨ Features

### Core Features

- ✅ **Event Sourcing**: All notifications are triggered by events
- ✅ **Idempotent Processing**: Duplicate events are automatically filtered
- ✅ **Rate Limiting**: Redis-based rate limiting (configurable per channel)
- ✅ **Retry Logic**: Failed notifications retry with exponential backoff
- ✅ **DLQ Handling**: Persistent failed messages for troubleshooting
- ✅ **Multi-Channel**: Email and SMS support with extensible design
- ✅ **Database Tracking**: Full audit trail of all notifications
- ✅ **Docker Support**: Fully containerized setup

### Reliability Features

- **Guaranteed Delivery**: At-least-once delivery semantics
- **Fault Tolerance**: Service continues even if individual notifications fail
- **Circuit Breaker**: Prevents cascade failures
- **Health Checks**: Service health monitoring
- **Graceful Shutdown**: Proper cleanup on service termination

## 🏛️ Architecture

### System Components

1. **Producer Service**: Generates notification events from various application triggers
2. **Notification Service**: Consumes events and processes notifications
3. **Apache Kafka**: Message broker for event streaming
4. **Redis**: Caching, idempotency checks, and rate limiting
5. **PostgreSQL**: Persistent storage for notification records
6. **Kafdrop**: Web UI for Kafka monitoring

### Data Flow

1. Application event triggers → Producer Service
2. Producer publishes event → Kafka Topic (`notifications`)
3. Notification Service consumes → Event from Kafka
4. Idempotency check → Redis (prevent duplicates)
5. Rate limit check → Redis (enforce limits)
6. Send notification → Email/SMS Service
7. Update status → PostgreSQL Database
8. On failure → Retry Handler → DLQ (if max retries exceeded)

## 🛠️ Tech Stack

### Backend

- **Node.js** (v18+)
- **TypeScript**
- **Prisma ORM** (v6.19.1)
- **KafkaJS** (v2.2.4)
- **Redis** (v5.10.0)
- **Nodemailer** (v7.0.12)

### Infrastructure

- **Apache Kafka** (v7.5.0)
- **Apache Zookeeper** (v7.5.0)
- **PostgreSQL** (via Prisma)
- **Redis** (v7)
- **Docker & Docker Compose**
- **Kafdrop** (Kafka UI)
