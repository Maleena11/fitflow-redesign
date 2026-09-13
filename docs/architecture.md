# FitFlow System Architecture

## 1. Overview

The FitFlow redesign uses a modular client-server architecture.

The system contains:

1. Mobile application
2. Web application
3. API/backend service
4. AI service
5. PostgreSQL database
6. Redis cache
7. Authentication service
8. Object storage
9. Real-time communication service

---

# 2. High-Level Architecture

```text
                    ┌─────────────────────┐
                    │       Users         │
                    └──────────┬──────────┘
                               │
                ┌──────────────┴──────────────┐
                │                             │
                ▼                             ▼
       ┌─────────────────┐          ┌─────────────────┐
       │ React Native    │          │ React / Next.js │
       │ Mobile App      │          │ Web Application │
       └────────┬────────┘          └────────┬────────┘
                │                            │
                └──────────────┬─────────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ API / Load Balancer │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ NestJS Backend      │
                    │                     │
                    │ Auth                │
                    │ Users               │
                    │ Workouts            │
                    │ Nutrition           │
                    │ Social              │
                    │ Challenges          │
                    │ Notifications       │
                    └──────┬──────┬───────┘
                           │      │
              ┌────────────┘      └─────────────┐
              ▼                                ▼
    ┌──────────────────┐              ┌──────────────────┐
    │   PostgreSQL     │              │      Redis       │
    │   Main Database  │              │ Cache / Sessions │
    └──────────────────┘              └──────────────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ FastAPI AI       │
                  │ Service          │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ AI/ML Models     │
                  │ TensorFlow/PyTorch│
                  └──────────────────┘
