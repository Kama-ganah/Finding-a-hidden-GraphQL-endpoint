# Overview
As a penetration tester, I assessed the application to identify undocumented or hidden API surfaces that could expose sensitive backend functionality. During testing, I discovered a hidden GraphQL endpoint that lacked proper access controls and relied on weak introspection filtering. By probing common endpoint paths and crafting custom GraphQL queries, I was able to enumerate the schema, identify sensitive mutations, and delete a user account without authentication. This project demonstrates how poorly secured GraphQL endpoints can be abused to perform unauthorized administrative actions.

# Steps Undertaken

Step 1: Probed common API and GraphQL endpoint paths and identified /api as a potential GraphQL endpoint based on error responses.

Step 2: Confirmed GraphQL functionality by issuing a minimal query (__typename) and receiving a valid response.

Step 3: Attempted standard introspection and observed it was blocked by superficial filtering.

Step 4: Bypassed introspection restrictions using newline injection to evade regex-based defenses.

Step 5: Enumerated the full GraphQL schema and identified sensitive queries and mutations.

Step 6: Used schema information to locate user management operations and extract a valid user ID.

Step 7: Executed an unauthorized mutation to delete the target user and verified successful account deletion.

# Conclusion

This assessment confirmed a high-severity vulnerability caused by an exposed GraphQL endpoint with inadequate introspection controls and missing authorization checks. The findings highlight the risks of relying on obscurity and weak filtering for API security, and emphasize the need for strict access control, proper schema protection, and hardened GraphQL configurations in production environments.
