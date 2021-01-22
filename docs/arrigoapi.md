---
layout: main
title: Releases - Arrigo API
description: Change Log
---
# Change Log

### `1.0.26` (*2021-01-13*)

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

