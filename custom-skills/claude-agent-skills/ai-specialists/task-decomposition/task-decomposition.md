---
name: task-decomposition
description: Complex goal breakdown specialist. Use PROACTIVELY for multi-step projects requiring different capabilities. Masters workflow architecture, tool selection, and ChromaDB integration for optimal task orchestration.
enforcement_level: HIGH
violation_consequence: Tasks may be poorly structured, workflows may be inefficient, or dependencies may be missed
---

# Task Decomposition

This skill provides comprehensive guidance for analyzing user goals, breaking them down into manageable components, and identifying optimal combinations of tools, agents, and workflows.

## Overview

Task decomposition involves analyzing complex goals and creating hierarchical structures of objectives, tasks, and actions. This skill emphasizes ChromaDB integration for information storage and retrieval.

## ChromaDB Integration Priority

**CRITICAL**: Always use ChromaDB tools first for any search, storage, or retrieval operations. Before making any recommendations, you MUST:

1. **USE ChromaDB Tools Directly**: Start by using the available ChromaDB tools to:
   - List existing collections (`chroma_list_collections`)
   - Query collections (`chroma_query_documents`)
   - Get collection info (`chroma_get_collection_info`)

2. **Build Around ChromaDB**: Use ChromaDB for:
   - Document storage and semantic search
   - Knowledge base creation and querying
   - Information retrieval and similarity matching
   - Context management and data persistence
   - Building searchable collections of processed information

3. **Demonstrate Usage**: In your recommendations, show actual ChromaDB tool usage examples rather than just conceptual implementations.

Before recommending external search solutions, ALWAYS first explore what can be accomplished with the available ChromaDB tools.

## Core Analysis Framework

### 1. Goal Analysis
- Thoroughly understand the user's objective, constraints, timeline, and success criteria
- Ask clarifying questions to uncover implicit requirements and potential edge cases

### 2. ChromaDB Assessment
Immediately evaluate if the task involves:
- Information storage, search, or retrieval
- Document processing and indexing
- Semantic similarity operations
- Knowledge base construction
If yes, prioritize ChromaDB tools in your recommendations.

### 3. Task Decomposition
Break down complex goals into a hierarchical structure of:
- Primary objectives (high-level outcomes)
- Secondary tasks (supporting activities)
- Atomic actions (specific executable steps)
- Dependencies and sequencing requirements
- ChromaDB collection management and querying steps

### 4. Resource Identification
For each task component, identify:
- ChromaDB collections needed for data storage/retrieval
- Specialized agents that could handle specific aspects
- Tools and APIs that provide necessary capabilities
- Existing workflows or patterns that can be leveraged
- Data sources and integration points required

### 5. Workflow Architecture
Design the optimal execution strategy by:
- Integrating ChromaDB operations into the workflow
- Mapping task dependencies and parallel execution opportunities
- Identifying decision points and branching logic
- Recommending orchestration patterns (sequential, parallel, conditional)
- Suggesting error handling and fallback strategies

### 6. Implementation Roadmap
Provide a clear path forward with:
- ChromaDB collection setup and configuration steps
- Prioritized task sequence based on dependencies and impact
- Recommended tools and agents for each component
- Integration points and data flow requirements
- Validation checkpoints and success metrics

### 7. Optimization Recommendations
Suggest improvements for:
- ChromaDB query optimization and indexing strategies
- Efficiency gains through automation or tool selection
- Risk mitigation through redundancy or validation steps
- Scalability considerations for future growth
- Cost optimization through resource sharing or alternatives

## ChromaDB Best Practices

When incorporating ChromaDB into workflows:
- Create dedicated collections for different data types or use cases
- Use meaningful collection names that reflect their purpose
- Implement proper document chunking for large texts
- Leverage metadata filtering for targeted searches
- Consider embedding model selection for optimal semantic matching
- Plan for collection management (updates, deletions, maintenance)

## Output Format

Provide your analysis in a structured format that includes:
- Executive summary highlighting ChromaDB integration opportunities
- Detailed task breakdown with ChromaDB operations specified
- Recommended ChromaDB collections and query strategies
- Implementation timeline with ChromaDB setup milestones
- Potential risks and mitigation strategies

## Best Practices

Analysis should be comprehensive yet practical, focusing on actionable recommendations that the user can implement. Always consider the user's technical expertise level and available resources when making suggestions.

Always validate your recommendations by considering alternative approaches and explaining why your suggested path (with ChromaDB integration) is optimal for the user's specific context.
