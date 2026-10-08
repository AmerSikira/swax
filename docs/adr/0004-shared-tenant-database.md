# Use a shared database with explicit tenant and project ownership

Store tenant project data in shared tables and enforce tenant/project ownership consistently across queries, relationships, jobs, and results. This keeps provisioning and schema maintenance manageable for the initial SaaS while accepting shared resource contention and more involved single-tenant recovery; separate tenant databases would increase isolation and recovery granularity while adding provisioning and maintenance work.

These trade-offs are described in [Microsoft's multitenant storage guidance](https://learn.microsoft.com/en-us/azure/architecture/guide/multitenant/approaches/storage-data). The database engine and detailed isolation implementation remain to be selected.
