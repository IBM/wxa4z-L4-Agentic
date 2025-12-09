# Summary of **zRAG Agent** capabilities

The **zRAG Agent** provides technical support for mainframe and enterprise systems through the Watson Assistant for Z chat interface. It leverages the zRAG (z/OS Retrieval-Augmented Generation) knowledge base to deliver accurate, citation-backed responses by integrating with IBM's documentation repositories and custom enterprise documentation.


Below is a summary of the agent capabilities.

**Agent capbility** | **Description**
--- | ---
**Document retrieval** | Queries the zRAG backend to fetch relevant technical documentation from IBM docs, Redbooks, and custom enterprise content
**Health monitoring** | Performs health checks on the zRAG MCP server, returning server status and configuration information
**AI-powered answers with citations** | Generates comprehensive, expert-level answers grounded in retrieved documentation with automatic inline citations and reference sections
**Compact responses for agents** | Provides streamlined responses optimized for multi-turn agent conversations, reducing token usage by 80% while maintaining answer quality
**Streaming responses** | Delivers real-time token-by-token generation for improved user experience
**Multi-source knowledge base** | Searches across IBM product documentation, Redbooks, customer-specific docs, and agent documentation with configurable weights
