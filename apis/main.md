# Fides API Documentation

This document provides an overview of the Fides API, including general information, base URL conventions, authentication requirements, and links to specific API sections.

---

## Overview

The Fides API provides a comprehensive set of endpoints for managing users, devices, services, smart contracts, buildings, notifications, and more within the Fides platform. It is designed to facilitate interaction with various resources, enabling developers to build applications that integrate with Fides' IoT and smart contract ecosystem.

---

## Base URL

All API endpoints are relative to the base URL:

```
https://your-domain.com
```

Each API section has its own base path, such as `/app/v1/user` for user-related endpoints or `/app/v1/device` for device-related endpoints. Refer to the specific section for the exact base path.

---

## Authentication

Most endpoints require a bearer token for authentication. Include the token in the `Authorization` header as follows:

```bash
Authorization: Bearer <token>
```

Some endpoints, such as certain authentication routes (e.g., Google login), may not require a token. Check the specific section for details.

---

## API Sections

The Fides API is organized into the following sections:

1. **[Users API](users.md)**: Manage user accounts, including creation, updates, and role assignments.
2. **[Buildings API](buildings.md)**: Handle building-related operations, such as creating and editing buildings with floors and units.
3. **[Authentication API](authentication.md)**: Manage authentication processes, including Google token verification and login callbacks.
4. **[Device Logs API](device-logs.md)**: Retrieve logs for devices based on encrypted IDs, user IDs, or shared devices.
5. **[Devices API](devices.md)**: Manage devices, including insertion, editing, sharing, and deletion.
6. **[Services API](services.md)**: Create and manage user services, including publishing and editing.
7. **[Smart Contract API](smart-contract.md)**: Handle smart contract operations, such as creation, publishing, and deletion.
8. **[MQTT Logs API](mqtt-logs.md)**: Retrieve MQTT logs for devices by device ID or user ID.
9. **[Theme API](theme.md)**: Manage user-specific themes and their settings.
10. **[Installed Services API](installed-services.md)**: Handle installation and management of services for users.
11. **[Notifications API](notifications.md)**: Manage user notifications, including retrieval, marking as read, and deletion.
12. **[Device Types API](device-types.md)**: Manage device types, including creation, editing, and deletion.
13. **[Subscriptions API](subscriptions.md)**: Manage user subscriptions, including creation, updates, and cancellations.

---

## Getting Started

To use the Fides API, obtain a bearer token through the authentication endpoints (see [Authentication API](authentication.md)). Replace `your-domain.com` with the actual domain of the Fides API instance. Each section provides detailed endpoint descriptions, request/response formats, and example cURL commands.

For pricing or subscription plan details, refer to the official Fides documentation or contact support, as this information is not covered in the API endpoints.

---

## Security

Unless otherwise specified, all endpoints require a bearer token. Ensure your token is valid and has the necessary permissions for the requested operation.

---
