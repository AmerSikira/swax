# Use durable records and retained input versions for AI continuity

Store project context and history as durable database records, and record the input versions used by each analysis so recommendations remain explainable after project information changes. Assemble relevant context for each AI request and rebuild summaries from retained records; this preserves continuity across users and providers and supports tracing recommendations back to their evidence.
