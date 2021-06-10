# fastify

-   Fastify works by dividing the service up into plugins
    -   A plugin is a module that exports a function
    -   The exported function is passed a fastify instance and options
    -   What we've created here is a route plugin (as opposed to a library plugin, which would go into the plugins folder)
