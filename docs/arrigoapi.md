---
layout: main
title: Releases - Arrigo API
description: Change Log
---
# Change Log

## 1.0.49

*2021-10-14* 

##### Features

- Hotfix: Consumptions Query (#358)
- Hotfix: Updated OrderBy for Credentials (#357)
- Hotfix: User Admin Create/Update fix (#356)

## 1.0.46

*2021-09-20* 

##### Features

User and access capabilities

Improved logging

Permissions for meter values

HotFix: Tree issue (#348)

Hotfix:MeterUnit fx for tsc (#350)

TimeZone for containers fixed malfunction in calculations of metervalues



## 1.0.27

*2021-01-28*

**Features**

- Log mutations
  Mutations are loged. 

  ```
   query MyQuery {
    mutationlog
  }
  ```

## 1.0.26

*2021-01-13*

**Features**
- Implement GQL query resolve tree.
> We can now alter queries by what's being asked for in the GQL query

**Fixes**
- Now verifying account on all UID decodings.
- Refactor Consumption filters to not query DB twice.

**Changes**

- Now using constants where possible.
- `ReadUID()` Now takes an account name to verify UID against.
- Added ENV (prod, beta, ...) to GQL error responses.
- Upper limit of 20K results per query.
- Reduce logging on slow queries (slowed response times significantly when logging so much)

