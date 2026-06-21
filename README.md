# LangGraph Interview Questions & Answers

> A curated list of LangGraph interview questions covering Fundamentals, Core Concepts, State Management, Reducers & Message State, Nodes & Best Practices, Conditional Edges & Routing, Command & Send, Agents & Tool Calling, Persistence & Checkpointing, Memory, Human-in-the-Loop, Streaming, Error Handling & Reliability, Subgraphs & Multi-Agent Systems, RAG with LangGraph, Testing, Observability & Monitoring, and Deployment & Production — each with a clear explanation and Python code example where applicable.

---

### Table of Contents

<details open>
<summary>
Hide/Show table of contents
</summary>

| No. | Questions |
| --- | --------- |
|     | **LangGraph Fundamentals** |
| 1 | [What is LangGraph?](#what-is-langgraph) |
| 2 | [Why is LangGraph used for building AI agents?](#why-is-langgraph-used-for-building-ai-agents) |
| 3 | [How is LangGraph different from LangChain?](#how-is-langgraph-different-from-langchain) |
| 4 | [How is LangGraph different from a normal sequential chain?](#how-is-langgraph-different-from-a-normal-sequential-chain) |
| 5 | [What problems does LangGraph solve in production AI systems?](#what-problems-does-langgraph-solve-in-production-ai-systems) |
| 6 | [What is meant by stateful agent orchestration?](#what-is-meant-by-stateful-agent-orchestration) |
| 7 | [Why are graphs useful for agent workflows?](#why-are-graphs-useful-for-agent-workflows) |
| 8 | [What is the role of nodes in LangGraph?](#what-is-the-role-of-nodes-in-langgraph) |
| 9 | [What is the role of edges in LangGraph?](#what-is-the-role-of-edges-in-langgraph) |
| 10 | [What is the difference between deterministic and agentic workflows in LangGraph?](#what-is-the-difference-between-deterministic-and-agentic-workflows-in-langgraph) |
| 11 | [When would you choose LangGraph over a simple LangChain chain?](#when-would-you-choose-langgraph-over-a-simple-langchain-chain) |
| 12 | [When should you avoid using LangGraph?](#when-should-you-avoid-using-langgraph) |
| 13 | [What is a long-running agent in LangGraph?](#what-is-a-long-running-agent-in-langgraph) |
| 14 | [What makes LangGraph suitable for production-grade agents?](#what-makes-langgraph-suitable-for-production-grade-agents) |
| 15 | [What are the main building blocks of a LangGraph application?](#what-are-the-main-building-blocks-of-a-langgraph-application) |
| 16 | [What is the difference between workflow orchestration and agent orchestration?](#what-is-the-difference-between-workflow-orchestration-and-agent-orchestration) |
| 17 | [How does LangGraph help with control flow in LLM applications?](#how-does-langgraph-help-with-control-flow-in-llm-applications) |
| 18 | [What is the relationship between LangGraph and LangChain models/tools?](#what-is-the-relationship-between-langgraph-and-langchain-modelstools) |
| 19 | [Can LangGraph be used without LangChain?](#can-langgraph-be-used-without-langchain) |
| 20 | [What are common real-world use cases for LangGraph?](#what-are-common-real-world-use-cases-for-langgraph) |
|     | **Core Concepts: Graph, Nodes & Edges** |
| 21 | [What is StateGraph in LangGraph?](#what-is-stategraph-in-langgraph) |
| 22 | [What is a compiled graph?](#what-is-a-compiled-graph) |
| 23 | [What happens when you call compile() on a graph?](#what-happens-when-you-call-compile-on-a-graph) |
| 24 | [What is the purpose of START in LangGraph?](#what-is-the-purpose-of-start-in-langgraph) |
| 25 | [What is the purpose of END in LangGraph?](#what-is-the-purpose-of-end-in-langgraph) |
| 26 | [How do you define a node in LangGraph?](#how-do-you-define-a-node-in-langgraph) |
| 27 | [What should a LangGraph node return?](#what-should-a-langgraph-node-return) |
| 28 | [What is the difference between a node and a tool?](#what-is-the-difference-between-a-node-and-a-tool) |
| 29 | [How do you add an edge between two nodes?](#how-do-you-add-an-edge-between-two-nodes) |
| 30 | [What is the difference between normal edges and conditional edges?](#what-is-the-difference-between-normal-edges-and-conditional-edges) |
| 31 | [What happens if a graph has no path to END?](#what-happens-if-a-graph-has-no-path-to-end) |
| 32 | [Can a LangGraph workflow contain cycles?](#can-a-langgraph-workflow-contain-cycles) |
| 33 | [Why are cycles important in agent workflows?](#why-are-cycles-important-in-agent-workflows) |
| 34 | [How does LangGraph prevent uncontrolled infinite loops?](#how-does-langgraph-prevent-uncontrolled-infinite-loops) |
| 35 | [What is graph invocation?](#what-is-graph-invocation) |
| 36 | [What is the difference between invoke() and stream()?](#what-is-the-difference-between-invoke-and-stream) |
| 37 | [What is the difference between graph input state and internal state?](#what-is-the-difference-between-graph-input-state-and-internal-state) |
| 38 | [What is the difference between graph output and final state?](#what-is-the-difference-between-graph-output-and-final-state) |
| 39 | [How do you visualise or inspect a LangGraph graph?](#how-do-you-visualise-or-inspect-a-langgraph-graph) |
| 40 | [How do you debug graph execution flow?](#how-do-you-debug-graph-execution-flow) |
|     | **State Management** |
| 41 | [What is state in LangGraph?](#what-is-state-in-langgraph) |
| 42 | [Why is state central to LangGraph?](#why-is-state-central-to-langgraph) |
| 43 | [How is state passed between nodes?](#how-is-state-passed-between-nodes) |
| 44 | [What is a state schema?](#what-is-a-state-schema) |
| 45 | [How do you define state using TypedDict?](#how-do-you-define-state-using-typeddict) |
| 46 | [How do you define state using Pydantic models?](#how-do-you-define-state-using-pydantic-models) |
| 47 | [What are the advantages of using typed state?](#what-are-the-advantages-of-using-typed-state) |
| 48 | [What happens when a node returns a partial state update?](#what-happens-when-a-node-returns-a-partial-state-update) |
| 49 | [Why should nodes usually return only updated fields?](#why-should-nodes-usually-return-only-updated-fields) |
| 50 | [What is the difference between replacing state and merging state?](#what-is-the-difference-between-replacing-state-and-merging-state) |
|     | **Reducers & Message State** |
| 51 | [What are reducers in LangGraph?](#what-are-reducers-in-langgraph) |
| 52 | [Why are reducers needed for concurrent node updates?](#why-are-reducers-needed-for-concurrent-node-updates) |
| 53 | [How does LangGraph handle multiple updates to the same state key?](#how-does-langgraph-handle-multiple-updates-to-the-same-state-key) |
| 54 | [What is the default behaviour when no reducer is defined?](#what-is-the-default-behaviour-when-no-reducer-is-defined) |
| 55 | [How do you append messages to a state field?](#how-do-you-append-messages-to-a-state-field) |
| 56 | [What is MessagesState?](#what-is-messagesstate) |
| 57 | [When would you use a custom state schema instead of MessagesState?](#when-would-you-use-a-custom-state-schema-instead-of-messagesstate) |
| 58 | [How do you manage conversation history in state?](#how-do-you-manage-conversation-history-in-state) |
| 59 | [What are common mistakes in LangGraph state design?](#what-are-common-mistakes-in-langgraph-state-design) |
| 60 | [How do you keep state small and efficient?](#how-do-you-keep-state-small-and-efficient) |
|     | **Nodes & Best Practices** |
| 61 | [What makes a good LangGraph node?](#what-makes-a-good-langgraph-node) |
| 62 | [Should nodes be small or large in LangGraph?](#should-nodes-be-small-or-large-in-langgraph) |
| 63 | [How do you separate business logic from graph orchestration?](#how-do-you-separate-business-logic-from-graph-orchestration) |
| 64 | [Can a node call an LLM?](#can-a-node-call-an-llm) |
| 65 | [Can a node call an external API?](#can-a-node-call-an-external-api) |
| 66 | [Can a node call another graph?](#can-a-node-call-another-graph) |
| 67 | [What should happen if a node fails?](#what-should-happen-if-a-node-fails) |
| 68 | [How do you design idempotent nodes?](#how-do-you-design-idempotent-nodes) |
| 69 | [Why is idempotency important in retryable workflows?](#why-is-idempotency-important-in-retryable-workflows) |
| 70 | [How do you avoid side effects inside LangGraph nodes?](#how-do-you-avoid-side-effects-inside-langgraph-nodes) |
|     | **Conditional Edges & Routing** |
| 71 | [What is a conditional edge?](#what-is-a-conditional-edge) |
| 72 | [How do conditional edges enable routing?](#how-do-conditional-edges-enable-routing) |
| 73 | [How do you route based on LLM output?](#how-do-you-route-based-on-llm-output) |
| 74 | [How do you route based on tool results?](#how-do-you-route-based-on-tool-results) |
| 75 | [How do you route based on user intent?](#how-do-you-route-based-on-user-intent) |
| 76 | [What should a routing function return?](#what-should-a-routing-function-return) |
| 77 | [How do you handle unknown routes?](#how-do-you-handle-unknown-routes) |
| 78 | [What is a fallback route?](#what-is-a-fallback-route) |
| 79 | [How do you avoid complex routing logic becoming unmaintainable?](#how-do-you-avoid-complex-routing-logic-becoming-unmaintainable) |
| 80 | [How do you test node routing independently?](#how-do-you-test-node-routing-independently) |
|     | **Command & Send** |
| 81 | [What is Command in LangGraph?](#what-is-command-in-langgraph) |
| 82 | [How is Command different from a conditional edge?](#how-is-command-different-from-a-conditional-edge) |
| 83 | [When should you use Command instead of normal routing?](#when-should-you-use-command-instead-of-normal-routing) |
| 84 | [How can Command update state and route simultaneously?](#how-can-command-update-state-and-route-simultaneously) |
| 85 | [What is Send in LangGraph?](#what-is-send-in-langgraph) |
| 86 | [When would you use Send?](#when-would-you-use-send) |
| 87 | [How does Send support map-reduce style workflows?](#how-does-send-support-map-reduce-style-workflows) |
| 88 | [How do you dynamically create parallel branches in LangGraph?](#how-do-you-dynamically-create-parallel-branches-in-langgraph) |
| 89 | [How do you aggregate results from multiple dynamically spawned tasks?](#how-do-you-aggregate-results-from-multiple-dynamically-spawned-tasks) |
| 90 | [What are common use cases for dynamic parallelism?](#what-are-common-use-cases-for-dynamic-parallelism) |
| 91 | [How would you process multiple documents in parallel using LangGraph?](#how-would-you-process-multiple-documents-in-parallel-using-langgraph) |
| 92 | [How would you fan out tasks and fan in results?](#how-would-you-fan-out-tasks-and-fan-in-results) |
| 93 | [How do reducers help with Send-based workflows?](#how-do-reducers-help-with-send-based-workflows) |
| 94 | [What can go wrong when multiple branches update the same state?](#what-can-go-wrong-when-multiple-branches-update-the-same-state) |
| 95 | [How do you control the number of dynamic tasks created?](#how-do-you-control-the-number-of-dynamic-tasks-created) |
| 96 | [How do you prevent excessive parallel execution?](#how-do-you-prevent-excessive-parallel-execution) |
| 97 | [How do you design a graph for batch processing?](#how-do-you-design-a-graph-for-batch-processing) |
| 98 | [How do you design a graph for multi-step document analysis?](#how-do-you-design-a-graph-for-multi-step-document-analysis) |
| 99 | [How do you design a graph that routes dynamically at runtime?](#how-do-you-design-a-graph-that-routes-dynamically-at-runtime) |
| 100 | [How do Command and Send improve graph flexibility?](#how-do-command-and-send-improve-graph-flexibility) |
|     | **Agents & Tool Calling** |
| 101 | [What is an agent in LangGraph?](#what-is-an-agent-in-langgraph) |
| 102 | [How do you build a ReAct-style agent in LangGraph?](#how-do-you-build-a-react-style-agent-in-langgraph) |
| 103 | [What is the difference between a workflow and an agent?](#what-is-the-difference-between-a-workflow-and-an-agent) |
| 104 | [How do you design an agent loop in LangGraph?](#how-do-you-design-an-agent-loop-in-langgraph) |
| 105 | [How do you decide when an agent should stop?](#how-do-you-decide-when-an-agent-should-stop) |
| 106 | [How do you prevent an agent from looping forever?](#how-do-you-prevent-an-agent-from-looping-forever) |
| 107 | [What is the role of the LLM node in an agent graph?](#what-is-the-role-of-the-llm-node-in-an-agent-graph) |
| 108 | [What is the role of the tool execution node?](#what-is-the-role-of-the-tool-execution-node) |
| 109 | [How does an agent decide which tool to call?](#how-does-an-agent-decide-which-tool-to-call) |
| 110 | [How do you handle invalid tool calls?](#how-do-you-handle-invalid-tool-calls) |
| 111 | [How do you handle tool execution errors?](#how-do-you-handle-tool-execution-errors) |
| 112 | [How do you return tool results back to the LLM?](#how-do-you-return-tool-results-back-to-the-llm) |
| 113 | [What is the difference between tool calling and function calling?](#what-is-the-difference-between-tool-calling-and-function-calling) |
| 114 | [How do you add multiple tools to a LangGraph agent?](#how-do-you-add-multiple-tools-to-a-langgraph-agent) |
| 115 | [How do you restrict which tools an agent can use?](#how-do-you-restrict-which-tools-an-agent-can-use) |
| 116 | [How do you design a safe tool-calling agent?](#how-do-you-design-a-safe-tool-calling-agent) |
| 117 | [How do you validate tool input before execution?](#how-do-you-validate-tool-input-before-execution) |
| 118 | [How do you handle tools with side effects?](#how-do-you-handle-tools-with-side-effects) |
| 119 | [How do you design an agent for customer support?](#how-do-you-design-an-agent-for-customer-support) |
| 120 | [How do you design an agent for code generation?](#how-do-you-design-an-agent-for-code-generation) |
|     | **Persistence & Checkpointing** |
| 121 | [What is checkpointing in LangGraph?](#what-is-checkpointing-in-langgraph) |
| 122 | [Why are checkpointers important?](#why-are-checkpointers-important) |
| 123 | [What information is stored in a checkpoint?](#what-information-is-stored-in-a-checkpoint) |
| 124 | [What is a thread in LangGraph?](#what-is-a-thread-in-langgraph) |
| 125 | [What is thread_id used for?](#what-is-thread_id-used-for) |
| 126 | [How does LangGraph resume execution from a checkpoint?](#how-does-langgraph-resume-execution-from-a-checkpoint) |
| 127 | [What is the difference between short-term memory and checkpointed state?](#what-is-the-difference-between-short-term-memory-and-checkpointed-state) |
| 128 | [How do you persist conversation state across user sessions?](#how-do-you-persist-conversation-state-across-user-sessions) |
| 129 | [What happens if no checkpointer is configured?](#what-happens-if-no-checkpointer-is-configured) |
| 130 | [How do checkpointers support fault tolerance?](#how-do-checkpointers-support-fault-tolerance) |
| 131 | [How do checkpointers support human-in-the-loop workflows?](#how-do-checkpointers-support-human-in-the-loop-workflows) |
| 132 | [What are common checkpoint backends?](#what-are-common-checkpoint-backends) |
| 133 | [When would you use an in-memory checkpointer?](#when-would-you-use-an-in-memory-checkpointer) |
| 134 | [Why is an in-memory checkpointer not suitable for production?](#why-is-an-in-memory-checkpointer-not-suitable-for-production) |
| 135 | [How would you use PostgreSQL or Redis for checkpointing?](#how-would-you-use-postgresql-or-redis-for-checkpointing) |
| 136 | [How do you manage checkpoint storage growth?](#how-do-you-manage-checkpoint-storage-growth) |
| 137 | [How do you clean up old checkpoints?](#how-do-you-clean-up-old-checkpoints) |
| 138 | [How do you handle checkpoint schema changes?](#how-do-you-handle-checkpoint-schema-changes) |
| 139 | [How do you version graph state?](#how-do-you-version-graph-state) |
| 140 | [How do you debug state using checkpoints?](#how-do-you-debug-state-using-checkpoints) |
|     | **Memory** |
| 141 | [What is memory in LangGraph?](#what-is-memory-in-langgraph) |
| 142 | [What is the difference between checkpointing and memory?](#what-is-the-difference-between-checkpointing-and-memory) |
| 143 | [What is short-term memory in LangGraph agents?](#what-is-short-term-memory-in-langgraph-agents) |
| 144 | [What is long-term memory in LangGraph agents?](#what-is-long-term-memory-in-langgraph-agents) |
| 145 | [What is a persistent store in LangGraph?](#what-is-a-persistent-store-in-langgraph) |
| 146 | [How do you store user preferences across sessions?](#how-do-you-store-user-preferences-across-sessions) |
| 147 | [How do you retrieve relevant memory during graph execution?](#how-do-you-retrieve-relevant-memory-during-graph-execution) |
| 148 | [How do you prevent memory from becoming noisy?](#how-do-you-prevent-memory-from-becoming-noisy) |
| 149 | [How do you decide what information should be saved to memory?](#how-do-you-decide-what-information-should-be-saved-to-memory) |
| 150 | [How do you delete or update stored memory?](#how-do-you-delete-or-update-stored-memory) |
| 151 | [How do you design memory for a personal assistant agent?](#how-do-you-design-memory-for-a-personal-assistant-agent) |
| 152 | [How do you design memory for enterprise support agents?](#how-do-you-design-memory-for-enterprise-support-agents) |
| 153 | [How do you handle sensitive data in memory?](#how-do-you-handle-sensitive-data-in-memory) |
| 154 | [How do you separate user-specific memory from global memory?](#how-do-you-separate-user-specific-memory-from-global-memory) |
| 155 | [How do you test memory behaviour in LangGraph?](#how-do-you-test-memory-behaviour-in-langgraph) |
|     | **Human-in-the-Loop** |
| 156 | [What is human-in-the-loop execution in LangGraph?](#what-is-human-in-the-loop-execution-in-langgraph) |
| 157 | [What is an interrupt in LangGraph?](#what-is-an-interrupt-in-langgraph) |
| 158 | [When would you interrupt before a node?](#when-would-you-interrupt-before-a-node) |
| 159 | [When would you interrupt after a node?](#when-would-you-interrupt-after-a-node) |
| 160 | [How do you resume a graph after human approval?](#how-do-you-resume-a-graph-after-human-approval) |
| 161 | [How do you design an approval workflow in LangGraph?](#how-do-you-design-an-approval-workflow-in-langgraph) |
| 162 | [How do you allow a human to edit state before resuming?](#how-do-you-allow-a-human-to-edit-state-before-resuming) |
| 163 | [How do you review tool calls before execution?](#how-do-you-review-tool-calls-before-execution) |
| 164 | [How do you handle rejected human approval?](#how-do-you-handle-rejected-human-approval) |
| 165 | [How do you design a graph for compliance review?](#how-do-you-design-a-graph-for-compliance-review) |
| 166 | [How do you design a graph for financial transaction approval?](#how-do-you-design-a-graph-for-financial-transaction-approval) |
| 167 | [How do you prevent unauthorized graph resumes?](#how-do-you-prevent-unauthorized-graph-resumes) |
| 168 | [How do interrupts depend on checkpointing?](#how-do-interrupts-depend-on-checkpointing) |
| 169 | [How do you audit human decisions in LangGraph?](#how-do-you-audit-human-decisions-in-langgraph) |
| 170 | [What are common human-in-the-loop design mistakes?](#what-are-common-human-in-the-loop-design-mistakes) |
|     | **Streaming** |
| 171 | [What is streaming in LangGraph?](#what-is-streaming-in-langgraph) |
| 172 | [What are streaming modes in LangGraph?](#what-are-streaming-modes-in-langgraph) |
| 173 | [What is the difference between streaming values and updates?](#what-is-the-difference-between-streaming-values-and-updates) |
| 174 | [What is message streaming?](#what-is-message-streaming) |
| 175 | [What is custom event streaming?](#what-is-custom-event-streaming) |
| 176 | [What is debug streaming?](#what-is-debug-streaming) |
| 177 | [How do you stream intermediate graph outputs to a UI?](#how-do-you-stream-intermediate-graph-outputs-to-a-ui) |
| 178 | [How do you stream token output from an LLM node?](#how-do-you-stream-token-output-from-an-llm-node) |
| 179 | [How do you show progress for a multi-step graph?](#how-do-you-show-progress-for-a-multi-step-graph) |
| 180 | [How do you stream tool execution status?](#how-do-you-stream-tool-execution-status) |
| 181 | [How do you handle streaming errors?](#how-do-you-handle-streaming-errors) |
| 182 | [How do you design a responsive chat UI with LangGraph?](#how-do-you-design-a-responsive-chat-ui-with-langgraph) |
| 183 | [How do you stream partial results from parallel branches?](#how-do-you-stream-partial-results-from-parallel-branches) |
| 184 | [How do you avoid exposing internal state in streamed output?](#how-do-you-avoid-exposing-internal-state-in-streamed-output) |
| 185 | [How do you test streaming behaviour?](#how-do-you-test-streaming-behaviour) |
|     | **Error Handling & Reliability** |
| 186 | [How do you handle node execution failures?](#how-do-you-handle-node-execution-failures) |
| 187 | [How do you configure retry policies in LangGraph?](#how-do-you-configure-retry-policies-in-langgraph) |
| 188 | [When should a node be retried?](#when-should-a-node-be-retried) |
| 189 | [When should a node not be retried?](#when-should-a-node-not-be-retried) |
| 190 | [How do you handle non-idempotent failures?](#how-do-you-handle-non-idempotent-failures) |
| 191 | [How do you implement fallback nodes?](#how-do-you-implement-fallback-nodes) |
| 192 | [How do you handle LLM timeout errors?](#how-do-you-handle-llm-timeout-errors) |
| 193 | [How do you handle tool timeout errors?](#how-do-you-handle-tool-timeout-errors) |
| 194 | [How do you handle rate limits from model providers?](#how-do-you-handle-rate-limits-from-model-providers) |
| 195 | [How do you recover from partial graph failure?](#how-do-you-recover-from-partial-graph-failure) |
| 196 | [How do checkpoints help with failure recovery?](#how-do-checkpoints-help-with-failure-recovery) |
| 197 | [How do you implement circuit breaker behaviour in LangGraph?](#how-do-you-implement-circuit-breaker-behaviour-in-langgraph) |
| 198 | [How do you design dead-letter handling for failed tasks?](#how-do-you-design-dead-letter-handling-for-failed-tasks) |
| 199 | [How do you log graph failures for debugging?](#how-do-you-log-graph-failures-for-debugging) |
| 200 | [How do you make LangGraph workflows production reliable?](#how-do-you-make-langgraph-workflows-production-reliable) |
|     | **Subgraphs & Multi-Agent Systems** |
| 201 | [What is a subgraph in LangGraph?](#what-is-a-subgraph-in-langgraph) |
| 202 | [Why would you split a workflow into subgraphs?](#why-would-you-split-a-workflow-into-subgraphs) |
| 203 | [How do subgraphs improve maintainability?](#how-do-subgraphs-improve-maintainability) |
| 204 | [How do you pass state between parent graphs and subgraphs?](#how-do-you-pass-state-between-parent-graphs-and-subgraphs) |
| 205 | [How do you isolate subgraph state?](#how-do-you-isolate-subgraph-state) |
| 206 | [What is a supervisor agent?](#what-is-a-supervisor-agent) |
| 207 | [How do you design a multi-agent system in LangGraph?](#how-do-you-design-a-multi-agent-system-in-langgraph) |
| 208 | [What is the difference between supervisor-based and peer-to-peer multi-agent design?](#what-is-the-difference-between-supervisor-based-and-peer-to-peer-multi-agent-design) |
| 209 | [How do you route tasks between specialised agents?](#how-do-you-route-tasks-between-specialised-agents) |
| 210 | [How do you prevent agents from conflicting with each other?](#how-do-you-prevent-agents-from-conflicting-with-each-other) |
| 211 | [How do you aggregate outputs from multiple agents?](#how-do-you-aggregate-outputs-from-multiple-agents) |
| 212 | [How do you design a researcher-writer-reviewer workflow?](#how-do-you-design-a-researcher-writer-reviewer-workflow) |
| 213 | [How do you design a planner-executor agent?](#how-do-you-design-a-planner-executor-agent) |
| 214 | [How do you design a code-review multi-agent system?](#how-do-you-design-a-code-review-multi-agent-system) |
| 215 | [How do you debug multi-agent graph behaviour?](#how-do-you-debug-multi-agent-graph-behaviour) |
|     | **RAG with LangGraph** |
| 216 | [How do you build a RAG pipeline using LangGraph?](#how-do-you-build-a-rag-pipeline-using-langgraph) |
| 217 | [Why use LangGraph for RAG instead of a simple retrieval chain?](#why-use-langgraph-for-rag-instead-of-a-simple-retrieval-chain) |
| 218 | [How do you add query rewriting to a LangGraph RAG workflow?](#how-do-you-add-query-rewriting-to-a-langgraph-rag-workflow) |
| 219 | [How do you add document retrieval as a node?](#how-do-you-add-document-retrieval-as-a-node) |
| 220 | [How do you add reranking as a node?](#how-do-you-add-reranking-as-a-node) |
| 221 | [How do you add answer generation as a node?](#how-do-you-add-answer-generation-as-a-node) |
| 222 | [How do you add hallucination checking to a RAG graph?](#how-do-you-add-hallucination-checking-to-a-rag-graph) |
| 223 | [How do you add source validation to a RAG graph?](#how-do-you-add-source-validation-to-a-rag-graph) |
| 224 | [How do you handle no-context-found scenarios?](#how-do-you-handle-no-context-found-scenarios) |
| 225 | [How do you route between vector search and web search?](#how-do-you-route-between-vector-search-and-web-search) |
| 226 | [How do you implement corrective RAG using LangGraph?](#how-do-you-implement-corrective-rag-using-langgraph) |
| 227 | [How do you implement adaptive RAG using LangGraph?](#how-do-you-implement-adaptive-rag-using-langgraph) |
| 228 | [How do you implement agentic RAG using LangGraph?](#how-do-you-implement-agentic-rag-using-langgraph) |
| 229 | [How do you cache retrieval results in LangGraph?](#how-do-you-cache-retrieval-results-in-langgraph) |
| 230 | [How do you evaluate a LangGraph-based RAG system?](#how-do-you-evaluate-a-langgraph-based-rag-system) |
|     | **Testing** |
| 231 | [How do you unit test LangGraph nodes?](#how-do-you-unit-test-langgraph-nodes) |
| 232 | [How do you integration test a full graph?](#how-do-you-integration-test-a-full-graph) |
| 233 | [How do you mock LLM responses in LangGraph tests?](#how-do-you-mock-llm-responses-in-langgraph-tests) |
| 234 | [How do you test conditional routing?](#how-do-you-test-conditional-routing) |
| 235 | [How do you test graph state updates?](#how-do-you-test-graph-state-updates) |
| 236 | [How do you test human-in-the-loop flows?](#how-do-you-test-human-in-the-loop-flows) |
|     | **Observability & Monitoring** |
| 237 | [How do you trace LangGraph execution?](#how-do-you-trace-langgraph-execution) |
| 238 | [How do you use LangSmith with LangGraph?](#how-do-you-use-langsmith-with-langgraph) |
| 239 | [What metrics should you monitor for LangGraph agents?](#what-metrics-should-you-monitor-for-langgraph-agents) |
| 240 | [How do you monitor latency per node?](#how-do-you-monitor-latency-per-node) |
| 241 | [How do you monitor token usage in LangGraph workflows?](#how-do-you-monitor-token-usage-in-langgraph-workflows) |
| 242 | [How do you monitor tool failure rates?](#how-do-you-monitor-tool-failure-rates) |
|     | **Deployment & Production** |
| 243 | [How do you deploy a LangGraph application?](#how-do-you-deploy-a-langgraph-application) |
| 244 | [How do you scale LangGraph workers?](#how-do-you-scale-langgraph-workers) |
| 245 | [How do you manage graph versions in production?](#how-do-you-manage-graph-versions-in-production) |
| 246 | [How do you roll back a LangGraph deployment?](#how-do-you-roll-back-a-langgraph-deployment) |
| 247 | [How do you secure API keys used inside graph nodes?](#how-do-you-secure-api-keys-used-inside-graph-nodes) |
| 248 | [How do you protect user data in LangGraph state?](#how-do-you-protect-user-data-in-langgraph-state) |
| 249 | [How do you design LangGraph for high concurrency?](#how-do-you-design-langgraph-for-high-concurrency) |
| 250 | [How would you design a production-grade AI assistant using LangGraph end to end?](#how-would-you-design-a-production-grade-ai-assistant-using-langgraph-end-to-end) |

</details>

---

## LangGraph Fundamentals

1. ### What is LangGraph?

   LangGraph is a **Python framework built on top of LangChain** for orchestrating complex, stateful AI workflows using a **graph-based model**. Unlike a simple sequential chain, a LangGraph application consists of **nodes** connected by **edges**. Each node is a function that receives a shared state and returns a partial update to that state. By modelling workflows as graphs rather than linear sequences, LangGraph makes it easy to handle branching logic, loops, parallelism, and other advanced patterns needed for robust agentic applications.

   ```python
   from langgraph.graph import StateGraph, START, END
   from typing import TypedDict

   class State(TypedDict):
       topic: str
       result: str

   def generate(state: State) -> dict:
       return {"result": f"An essay about {state['topic']}"}

   builder = StateGraph(State)
   builder.add_node("generate", generate)
   builder.add_edge(START, "generate")
   builder.add_edge("generate", END)
   graph = builder.compile()

   print(graph.invoke({"topic": "the ocean"}))
   # {'topic': 'the ocean', 'result': 'An essay about the ocean'}
   ```

   **[⬆ Back to Top](#table-of-contents)**

2. ### Why is LangGraph used for building AI agents?

   Agents often need to manage long conversations, call multiple tools, branch based on intermediate results, pause for human approval, and maintain context across turns. A simple chain of functions is insufficient for these requirements. LangGraph introduces a **stateful graph model** where each node can update a shared conversation state and control flow can be conditional or cyclical. This makes it possible to build agents that **plan, execute tools, handle errors, and resume after pauses**, all within a structured workflow. The emphasis on **persistence and memory** distinguishes LangGraph from stateless pipelines.

   **[⬆ Back to Top](#table-of-contents)**

3. ### How is LangGraph different from LangChain?

   LangChain provides abstractions for LLMs, prompts, tools, and chains but lacks a native way to orchestrate complex workflows with loops and branching. LangGraph extends LangChain by adding a **graph abstraction**: you define a state schema, create nodes that operate on this state, connect them via edges (including conditional edges), and compile the graph into an executable object. LangGraph also integrates **persistence via checkpointers and stores**, making it suitable for long-running agents or chatbots where conversation context must survive between sessions.

   | Aspect | LangChain | LangGraph |
   | --- | --- | --- |
   | Primary abstraction | Chains (linear) | Graphs (nodes + edges) |
   | Control flow | Sequential | Branching, loops, parallel |
   | State | Implicit / passed along | Explicit shared state |
   | Persistence | Limited | Built-in checkpointers & stores |
   | Best for | Simple pipelines | Stateful agents |

   **[⬆ Back to Top](#table-of-contents)**

4. ### How is LangGraph different from a normal sequential chain?

   A normal sequential chain executes tasks in a **fixed order** with no branching or loops. In contrast, a LangGraph graph can **branch based on conditions, loop until a termination criterion is met, or execute multiple branches in parallel**. Nodes operate on a shared state and edges dictate control flow. This allows developers to model complex decision-making and iterative processes in a structured manner. For example, a ReAct agent might loop through an LLM node and a tool execution node until it decides to stop.

   **[⬆ Back to Top](#table-of-contents)**

5. ### What problems does LangGraph solve in production AI systems?

   Production AI agents often need to manage long conversations, handle interruptions, call external tools, and maintain context between sessions. LangGraph solves these problems by offering:

   - **Stateful orchestration** — each node reads and writes to a shared state.
   - **Control-flow primitives** — graphs support conditional edges, loops, and parallel branches.
   - **Persistence** — short-term memory via checkpointers and long-term memory via stores allow an agent to pause and resume or recall user-specific data.
   - **Interrupts** — human-in-the-loop workflows can pause execution and resume after human input.
   - **Streaming** — events can be streamed during execution to update a UI in real time.

   **[⬆ Back to Top](#table-of-contents)**

6. ### What is meant by stateful agent orchestration?

   Stateful agent orchestration refers to controlling an agent's behaviour based on a **shared state that accumulates information over time**. In LangGraph, the state is typically a dictionary or Pydantic model that stores the conversation history, tool results, flags, and other metadata. Each node in the graph receives the current state and returns a partial update; LangGraph then **merges these updates into the global state using reducers**. This pattern ensures that context is maintained throughout the workflow and can be persisted for later.

   **[⬆ Back to Top](#table-of-contents)**

7. ### Why are graphs useful for agent workflows?

   Graph structures are well suited for modelling workflows with **branching, looping, and concurrency**. An agent might need to decide between multiple tools based on the user's intent, then loop through tool calls until the job is done. A graph naturally expresses these paths with nodes and edges. Graphs also make it easier to **visualise and reason about** the flow of an agent, which is beneficial for debugging and extending complex systems.

   **[⬆ Back to Top](#table-of-contents)**

8. ### What is the role of nodes in LangGraph?

   Nodes are the **building blocks** of a LangGraph workflow. A node is essentially a function that takes the current state and returns a partial state update. Nodes can perform arbitrary logic such as calling LLMs, invoking tools, executing code, or making API calls. Because they operate on the state, nodes are easily composable and can be chained or branched as needed. Nodes should ideally be **idempotent and side-effect free** (or manage side effects carefully) to support retries.

   ```python
   def classify_intent(state: dict) -> dict:
       text = state["user_input"]
       intent = "billing" if "invoice" in text.lower() else "general"
       return {"intent": intent}
   ```

   **[⬆ Back to Top](#table-of-contents)**

9. ### What is the role of edges in LangGraph?

   Edges connect nodes and **determine the order of execution**. When you define `builder.add_edge("node_a", "node_b")`, LangGraph runs `node_a`, merges its state update, then runs `node_b` with the updated state. Edges can be **unconditional** (always lead to the target) or **conditional** (route based on a condition). Without edges, nodes would be isolated functions; edges turn them into a coherent workflow.

   ```python
   builder.add_edge("retrieve", "generate")   # unconditional
   builder.add_conditional_edges("planner", route_fn, {"search": "search_node", "done": END})
   ```

   **[⬆ Back to Top](#table-of-contents)**

10. ### What is the difference between deterministic and agentic workflows in LangGraph?

    **Deterministic workflows** have a fixed sequence of operations defined at graph construction time. **Agentic workflows** involve an agent making decisions based on model outputs, tool results, or human input — these need branching, loops, and dynamic control flow. LangGraph supports both types but **excels at agentic workflows** due to its flexible control-flow mechanisms and persistent state.

    | | Deterministic | Agentic |
    | --- | --- | --- |
    | Control flow | Fixed at build time | Decided at runtime |
    | Driven by | Predefined edges | LLM / tool outputs |
    | Loops | Rare | Common (ReAct) |
    | Example | ETL pipeline | Autonomous research agent |

    **[⬆ Back to Top](#table-of-contents)**

11. ### When would you choose LangGraph over a simple LangChain chain?

    Use LangGraph when your workflow requires **branching, looping, concurrency, long-term persistence, or human-in-the-loop steps**. A simple LangChain chain is suitable for straightforward pipelines where each step is performed exactly once in a fixed order. If your application needs to route based on model output, loop until a condition is met, pause for approval, or combine multiple parallel tasks, LangGraph is a better fit.

    **[⬆ Back to Top](#table-of-contents)**

12. ### When should you avoid using LangGraph?

    If your application is a **simple sequential chain** of operations with no branching, loops, or persistence requirements, using LangGraph may add unnecessary complexity. LangGraph also introduces overhead in terms of learning curve and execution complexity. For quick prototypes or one-off LLM calls, a simple LangChain chain or vanilla Python may suffice. Additionally, if your team already has a robust orchestration system or does not require stateful agents, LangGraph might not be necessary.

    **[⬆ Back to Top](#table-of-contents)**

13. ### What is a long-running agent in LangGraph?

    A long-running agent maintains state **across multiple turns and possibly across multiple user sessions**. In LangGraph, long-running agents leverage persistence: short-term memory is stored in checkpointers (for conversation continuity), and long-term memory is stored in persistent stores (for user preferences). Long-running agents can pause execution (via interrupts), wait for human input, then **resume from the previous state** without losing context.

    **[⬆ Back to Top](#table-of-contents)**

14. ### What makes LangGraph suitable for production-grade agents?

    Production-grade agents need **reliability, fault tolerance, observability, and the ability to handle complex flows**. LangGraph addresses these by providing state persistence, error handling, streaming, and modularity. Checkpointers enable resuming after crashes or human interruption, streaming exposes events for UIs and monitoring, and interrupts allow human-in-the-loop processes. These features make LangGraph well suited for production AI systems.

    **[⬆ Back to Top](#table-of-contents)**

15. ### What are the main building blocks of a LangGraph application?

    The main building blocks are:

    | Block | Purpose |
    | --- | --- |
    | **State schema** | Defines the structure of the shared state |
    | **Nodes** | Perform computations on the state |
    | **Edges** | Control the flow between nodes |
    | **Reducers** | Merge concurrent updates to the same key |
    | **Checkpointers / Stores** | Persist short-term and long-term memory |
    | **Compilation** | Finalises the graph structure for execution |

    **[⬆ Back to Top](#table-of-contents)**

16. ### What is the difference between workflow orchestration and agent orchestration?

    **Workflow orchestration** typically refers to deterministic sequences of tasks with defined dependencies (for instance, ETL pipelines). **Agent orchestration** involves orchestrating an AI agent's reasoning and actions, which can include loops, branching, and tool calls based on model outputs. LangGraph is designed for agent orchestration, enabling dynamic control flow and state management across multiple steps, unlike typical workflow orchestrators that are oriented around data processing tasks.

    **[⬆ Back to Top](#table-of-contents)**

17. ### How does LangGraph help with control flow in LLM applications?

    LangGraph introduces control-flow primitives such as **conditional edges, loops, parallel branches, `Command`, and `Send`**. These allow LLM applications to route execution based on the model's output or the results of tool calls. For example, an LLM node might return a label like `"search"` or `"summarize"`, and a routing function can use this to send control to the appropriate tool node. This **explicit control flow reduces prompt complexity** and makes the agent's logic easier to understand and debug.

    **[⬆ Back to Top](#table-of-contents)**

18. ### What is the relationship between LangGraph and LangChain models/tools?

    LangGraph **builds upon** LangChain's abstractions for models, prompts, tools, retrievers, etc. Nodes in a LangGraph graph often call LangChain LLMs or tools internally. For example, a node might use `ChatOpenAI` to generate text or a search tool wrapper to query the web. LangGraph **does not replace** these components — it orchestrates them. Think of LangChain as providing the components and LangGraph as providing the orchestration layer.

    ```python
    from langchain_openai import ChatOpenAI

    llm = ChatOpenAI(model="gpt-4o-mini", temperature=0)

    def summarize(state: dict) -> dict:
        response = llm.invoke(f"Summarize: {state['text']}")
        return {"summary": response.content}
    ```

    **[⬆ Back to Top](#table-of-contents)**

19. ### Can LangGraph be used without LangChain?

    **Yes.** Although LangGraph's examples often rely on LangChain components, nodes are **arbitrary functions** that operate on a state. If you prefer to use another model provider or custom logic, you can still write nodes that call external APIs or Python libraries directly. LangGraph's orchestration features such as state management and control flow do not depend on LangChain classes. However, using LangChain can reduce boilerplate when dealing with LLMs and tools.

    ```python
    import requests

    def call_custom_model(state: dict) -> dict:
        resp = requests.post("https://my-llm.internal/generate",
                             json={"prompt": state["prompt"]})
        return {"output": resp.json()["text"]}
    ```

    **[⬆ Back to Top](#table-of-contents)**

20. ### What are common real-world use cases for LangGraph?

    Common use cases include **customer support agents, coding assistants, research and summarisation workflows, data extraction and enrichment pipelines, and human-in-the-loop workflows**. LangGraph's support for persistence, branching, and loops makes it ideal for tasks requiring long conversations, iterative tool calls, and human approval steps.

    **[⬆ Back to Top](#table-of-contents)**


## Core Concepts: Graph, Nodes & Edges

21. ### What is StateGraph in LangGraph?

    `StateGraph` is the **primary class** used to build a graph in LangGraph. You instantiate it with a state schema and then add nodes and edges. Under the hood, `StateGraph` ensures that each node has a signature of `State -> Partial[State]` and merges updates using reducers. Once all nodes and edges are defined, you call `compile()` to create an executable graph.

    ```python
    from langgraph.graph import StateGraph, START, END
    from typing import TypedDict

    class State(TypedDict):
        count: int

    builder = StateGraph(State)
    builder.add_node("increment", lambda s: {"count": s["count"] + 1})
    builder.add_edge(START, "increment")
    builder.add_edge("increment", END)
    graph = builder.compile()
    ```

    **[⬆ Back to Top](#table-of-contents)**

22. ### What is a compiled graph?

    A compiled graph is the **executable form** of a LangGraph graph. When you call `builder.compile()`, LangGraph builds an internal representation of the nodes, edges, reducers, and checkpointer configuration. The compiled graph can then be invoked with an initial state using `invoke(input)` or streamed using `stream(input)`. Compiling helps **catch configuration errors early** and improves performance.

    **[⬆ Back to Top](#table-of-contents)**

23. ### What happens when you call compile() on a graph?

    During compilation, LangGraph:

    - Resolves the **state schema**.
    - Verifies that all **nodes and edges are valid**.
    - Ensures there is at least one path from `START` to `END`.
    - Wires up **reducers** for each state key.
    - **Freezes the graph definition** so nodes or edges cannot be added afterward.

    In other words, `compile()` finalises the graph's structure and prepares it for execution. You can also pass a `checkpointer` and `store` at this step.

    ```python
    graph = builder.compile(checkpointer=checkpointer, store=store)
    ```

    **[⬆ Back to Top](#table-of-contents)**

24. ### What is the purpose of START in LangGraph?

    `START` is a **special sentinel node** representing the entry point of a graph. When you compile a graph, `START`'s output is the initial state passed to the next node. Typically you connect `START` to the first logical node using `builder.add_edge(START, "first_node")`. `START` does not perform any computation; its state is the initial input provided when invoking the graph.

    **[⬆ Back to Top](#table-of-contents)**

25. ### What is the purpose of END in LangGraph?

    `END` is a **special sentinel node** representing the termination of the graph. When execution reaches `END`, LangGraph returns the current state as the final output. Every compiled graph must have a path from `START` to `END`; otherwise, `compile()` will raise an error. `END` acts as a signal to stop traversal.

    **[⬆ Back to Top](#table-of-contents)**

26. ### How do you define a node in LangGraph?

    You define a node by writing a function that accepts a state and returns a dictionary of updates:

    ```python
    def greet(state: dict) -> dict:
        name = state["name"]
        return {"greeting": f"Hello, {name}!"}

    builder.add_node("greet", greet)
    builder.add_edge(START, "greet")
    builder.add_edge("greet", END)
    ```

    Nodes can also be class methods or callables with additional arguments; the only requirement is that they take the current state as input and return a partial state update.

    **[⬆ Back to Top](#table-of-contents)**

27. ### What should a LangGraph node return?

    Nodes should return a **dictionary representing a partial update** to the state. The keys correspond to fields in the state schema, and the values are the new values for those fields. Nodes can update zero or more fields. They should **avoid mutating the input state directly**; instead, they return a new dictionary with updated keys. LangGraph then merges this update into the existing state using reducers where necessary.

    ```python
    # GOOD: return only updated fields, no mutation
    def add_result(state: dict) -> dict:
        return {"result": compute(state["input"])}

    # BAD: mutating input state directly
    def bad(state: dict) -> dict:
        state["result"] = compute(state["input"])  # avoid this
        return state
    ```

    **[⬆ Back to Top](#table-of-contents)**

28. ### What is the difference between a node and a tool?

    In LangChain, a **tool** is an object that performs a specific external action (e.g., an API call). In LangGraph, a **node** is a unit of computation that can call one or more tools, LLMs, or custom functions. Tools are typically stateless and focused on single operations, while nodes operate on and modify the **shared state**. You can wrap a tool call inside a node to update the state with the tool's result.

    | | Node | Tool |
    | --- | --- | --- |
    | Operates on | Shared graph state | Its own arguments |
    | Scope | Orchestration unit | Single external action |
    | Returns | Partial state update | Raw result |
    | Stateful | Yes (via state) | Usually stateless |

    **[⬆ Back to Top](#table-of-contents)**

29. ### How do you add an edge between two nodes?

    Use the `add_edge(source, target)` method on a `StateGraph` instance:

    ```python
    builder.add_edge("node_a", "node_b")
    ```

    This tells LangGraph to execute `node_a`, merge its state update, then execute `node_b` with the new state. You should ensure there is at least one path from `START` to `END` that covers all necessary nodes.

    **[⬆ Back to Top](#table-of-contents)**

30. ### What is the difference between normal edges and conditional edges?

    **Normal edges** always lead to the target node after the source node executes. **Conditional edges** allow branching based on a condition. In LangGraph, conditional edges are created using `add_conditional_edges(source, condition_fn, mapping)`, where `condition_fn` reads the state and returns a key, and `mapping` maps that key to a target node. The graph then routes to the appropriate node based on the returned key.

    ```python
    def route(state: dict) -> str:
        return "approved" if state["score"] > 0.8 else "rejected"

    builder.add_conditional_edges("review", route, {
        "approved": "publish",
        "rejected": "revise",
    })
    ```

    **[⬆ Back to Top](#table-of-contents)**

31. ### What happens if a graph has no path to END?

    LangGraph's **compilation will fail** with an error. A valid graph must have at least one path from `START` to `END` to guarantee termination. If you inadvertently create cycles without an exit or forget to add edges to `END`, the graph will not compile. This early error helps prevent workflows that would otherwise run indefinitely.

    **[⬆ Back to Top](#table-of-contents)**

32. ### Can a LangGraph workflow contain cycles?

    **Yes.** LangGraph allows cycles (loops) as long as there is still a path to `END` that can eventually be taken. Cycles are useful for agentic workflows where you loop through an LLM and tool until a goal is reached. However, you must provide a **termination condition**; otherwise, the graph could loop infinitely.

    ```python
    # Agent loop: planner -> tool -> planner -> ... -> END
    builder.add_conditional_edges("planner", should_continue, {
        "continue": "tool",
        "end": END,
    })
    builder.add_edge("tool", "planner")  # cycle back
    ```

    **[⬆ Back to Top](#table-of-contents)**

33. ### Why are cycles important in agent workflows?

    Cycles allow an agent to **iterate until some condition is met**, such as gathering more information or refining a plan. For example, a ReAct agent might alternately call the LLM to determine the next action and then call a tool, repeating until a "finished" flag is set. Without cycles, you would need to guess the number of iterations ahead of time or rely on a single prompt, which limits flexibility and performance.

    **[⬆ Back to Top](#table-of-contents)**

34. ### How does LangGraph prevent uncontrolled infinite loops?

    LangGraph does **not automatically prevent** infinite loops; it is the developer's responsibility to implement a termination condition. However, the framework provides a `recursion_limit` (default 25) that raises a `GraphRecursionError` when exceeded, acting as a safety net. Because the graph is explicit, you can easily identify cycles and ensure a conditional edge eventually routes to `END`.

    ```python
    graph.invoke(input_state, config={"recursion_limit": 50})
    ```

    **[⬆ Back to Top](#table-of-contents)**

35. ### What is graph invocation?

    Graph invocation refers to **running the compiled graph** with a given initial state. You call `compiled_graph.invoke(state_input)` to execute the workflow. LangGraph starts at `START`, follows edges, updates state at each node, and finishes at `END`, returning the final state. Invocation can be done synchronously, or you can use the streaming interface to receive intermediate updates.

    ```python
    final_state = graph.invoke({"topic": "AI safety"})
    ```

    **[⬆ Back to Top](#table-of-contents)**

36. ### What is the difference between invoke() and stream()?

    `invoke(input_state)` runs the graph **synchronously** and returns the **final state** once execution completes. `stream(input_state)` returns an **iterator of events**, yielding state updates and possibly custom events as the graph executes. Streaming is useful when you want to show intermediate results to a user or update a UI in real time.

    ```python
    # invoke — wait for the final result
    result = graph.invoke({"q": "hi"})

    # stream — process events as they arrive
    for event in graph.stream({"q": "hi"}, stream_mode="updates"):
        print(event)
    ```

    **[⬆ Back to Top](#table-of-contents)**

37. ### What is the difference between graph input state and internal state?

    The **input state** is the state you pass to `invoke()` or `stream()`. It must conform to the state schema and typically contains user-provided information. The **internal state** is the evolving state as nodes run and update it. Internal state includes initial fields plus any new fields added by nodes. At the end of execution, the internal state becomes the output state returned to the caller.

    **[⬆ Back to Top](#table-of-contents)**

38. ### What is the difference between graph output and final state?

    When `invoke()` returns, the **graph output is the final state** after all nodes have executed up to `END`. This state includes all fields defined in the state schema and any additional fields created during execution. In **streaming mode**, you may see intermediate states, but the final event corresponds to the state at `END`. You can also define separate input/output schemas to expose only specific fields to the caller.

    **[⬆ Back to Top](#table-of-contents)**

39. ### How do you visualise or inspect a LangGraph graph?

    LangGraph provides drawing utilities that render the graph structure (using Mermaid or Graphviz). You can also print the graph's node and edge lists for debugging. Visualisation helps verify control flow and ensure that conditional branches and cycles are correctly configured. Tools like **LangSmith** can also display graph execution traces.

    ```python
    # Render as Mermaid PNG (requires extra deps)
    png_bytes = graph.get_graph().draw_mermaid_png()
    with open("graph.png", "wb") as f:
        f.write(png_bytes)

    # Or print the Mermaid text definition
    print(graph.get_graph().draw_mermaid())
    ```

    **[⬆ Back to Top](#table-of-contents)**

40. ### How do you debug graph execution flow?

    To debug, you can **instrument nodes to log state updates** or print debug messages. Running the graph in **streaming mode** and printing each event is especially helpful — you see how the state evolves and which nodes execute. Additionally, LangGraph's error handling lets you catch exceptions inside nodes and either retry or route to a fallback node for diagnosis.

    ```python
    for event in graph.stream(input_state, stream_mode="debug"):
        print(event)  # node start/end, state merges, routing decisions
    ```

    **[⬆ Back to Top](#table-of-contents)**


## State Management

41. ### What is state in LangGraph?

    State is a **dictionary-like object** that holds all information relevant to the agent's workflow. It may include the user's messages, tool outputs, flags indicating whether the task is complete, memory buffers, and any other data you need to persist. The state is the **sole mechanism for passing information between nodes** — there are no hidden variables. This explicitness makes the flow of data easier to understand and debug.

    **[⬆ Back to Top](#table-of-contents)**

42. ### Why is state central to LangGraph?

    Because LangGraph orchestrates complex workflows with multiple nodes and branches, a **shared state is needed to maintain context**. Without a state, nodes would have to rely on global variables or hidden side effects, making the program fragile. By standardising on a state schema and requiring each node to return partial updates, LangGraph enforces a consistent pattern that promotes **reliability and maintainability**.

    **[⬆ Back to Top](#table-of-contents)**

43. ### How is state passed between nodes?

    When a node returns a partial state update, LangGraph **merges this update into the current state** and passes the new state to the next node. The merging process uses **reducers** to combine values if multiple nodes update the same key. For keys without reducers, the new value replaces the old value. This ensures that updates from different nodes do not overwrite each other unexpectedly.

    **[⬆ Back to Top](#table-of-contents)**

44. ### What is a state schema?

    The state schema **defines the keys and types** in the shared state. It can be a `TypedDict`, a Pydantic `BaseModel`, or a dataclass. The schema acts as documentation and ensures that nodes do not read or write undefined fields. Some checkpointers also use the schema to validate stored state.

    ```python
    from typing import TypedDict, Annotated
    from operator import add

    class State(TypedDict):
        question: str
        documents: list[str]
        messages: Annotated[list, add]  # reducer attached via Annotated
    ```

    **[⬆ Back to Top](#table-of-contents)**

45. ### How do you define state using TypedDict?

    You can define a `TypedDict` to describe the state shape. `TypedDict`s provide static type hints for a better developer experience and ensure that nodes operate on the correct fields:

    ```python
    from typing import TypedDict
    from langgraph.graph import StateGraph

    class AgentState(TypedDict):
        messages: list[str]
        result: str
        is_done: bool

    builder = StateGraph(AgentState)
    ```

    Nodes can then update `messages`, `result`, or `is_done` fields.

    **[⬆ Back to Top](#table-of-contents)**

46. ### How do you define state using Pydantic models?

    LangGraph accepts any Pydantic `BaseModel` as the state schema. Pydantic provides **validation, default values, and nested structures**:

    ```python
    from pydantic import BaseModel
    from langgraph.graph import StateGraph

    class AgentState(BaseModel):
        messages: list[str] = []
        result: str | None = None
        is_done: bool = False

    builder = StateGraph(AgentState)
    ```

    Pydantic models validate inputs at runtime, raising clear errors if a node returns the wrong type.

    **[⬆ Back to Top](#table-of-contents)**

47. ### What are the advantages of using typed state?

    Typed state **clarifies which keys are expected** and what types they should have. This reduces bugs due to misspelt keys or wrong types. IDEs can provide autocompletion and type checking. Typed state also helps checkpointers validate stored state and facilitates integration with static analysis tools like `mypy`.

    **[⬆ Back to Top](#table-of-contents)**

48. ### What happens when a node returns a partial state update?

    LangGraph **merges the update into the current state**. For keys with reducers, the reducer function is called to combine the previous value and the new value. For keys without reducers, the new value **replaces** the old value. If a node returns a key not defined in the state schema, LangGraph may raise an error or warning depending on the schema configuration.

    **[⬆ Back to Top](#table-of-contents)**

49. ### Why should nodes usually return only updated fields?

    Returning only updated fields **minimises accidental overwriting** of state. If a node returns the entire state, it could inadvertently override changes made by other nodes or force additional reducer calls. By returning only the fields it intends to modify, a node clarifies its behaviour and allows other nodes to update different fields independently. It also reduces the size of state updates, making persistence more efficient.

    **[⬆ Back to Top](#table-of-contents)**

50. ### What is the difference between replacing state and merging state?

    **Replacing state** means completely overwriting the previous state with a new one; **merging state** combines updates into the existing state. LangGraph **always merges** updates using reducers — there is no built-in way to replace the entire state. If you need to clear a field, set it to an empty value or use a reducer that implements clearing. Merging ensures that updates from different nodes do not erase each other unexpectedly.

    **[⬆ Back to Top](#table-of-contents)**


## Reducers & Message State

51. ### What are reducers in LangGraph?

    Reducers are **functions that define how to combine multiple updates** to the same state key. They are particularly important when nodes operate in parallel or when multiple branches update the same list or dictionary. In modern LangGraph, reducers are attached to a state field using `Annotated`:

    ```python
    from typing import Annotated, TypedDict
    from operator import add

    class State(TypedDict):
        # 'add' concatenates lists instead of overwriting
        messages: Annotated[list[str], add]

    def node_a(state): return {"messages": ["from A"]}
    def node_b(state): return {"messages": ["from B"]}
    # After both run, messages == ["from A", "from B"]
    ```

    Without a reducer, the most recent update would overwrite previous updates. Reducers give you fine-grained control over state merging.

    **[⬆ Back to Top](#table-of-contents)**

52. ### Why are reducers needed for concurrent node updates?

    When nodes execute **concurrently** (e.g., via `Send` or parallel branches), they may return updates to the same state field at roughly the same time. Without a reducer, whichever update is applied last would **overwrite** the earlier one. Reducers ensure that concurrent updates are combined predictably (e.g., appending to a list or merging dictionaries), preserving all contributions.

    **[⬆ Back to Top](#table-of-contents)**

53. ### How does LangGraph handle multiple updates to the same state key?

    LangGraph calls the **reducer registered for that key**. The reducer is passed the previous value and the new update(s) and returns the combined result. If no reducer is registered, the **last update wins** (the new value replaces the old). Therefore, to accumulate values or handle more complex merging, you should register reducers. Reducers can also implement custom logic like deduplication.

    ```python
    def dedup_merge(old: list, new: list) -> list:
        return list(dict.fromkeys(old + new))  # preserve order, drop dups

    class State(TypedDict):
        keywords: Annotated[list[str], dedup_merge]
    ```

    **[⬆ Back to Top](#table-of-contents)**

54. ### What is the default behaviour when no reducer is defined?

    If a state key has **no reducer**, the last update simply **overwrites** the previous value. In a deterministic graph with no concurrency, this may be acceptable. However, in concurrent scenarios, you risk losing updates if multiple nodes write to the same key. Defining reducers for list-like fields, counters, or aggregated objects is recommended.

    **[⬆ Back to Top](#table-of-contents)**

55. ### How do you append messages to a state field?

    Attach a reducer (such as `operator.add` or the built-in `add_messages`) to the field. Then nodes return `{"messages": [new_message]}` and LangGraph appends it to the existing list:

    ```python
    from langgraph.graph.message import add_messages
    from typing import Annotated, TypedDict

    class State(TypedDict):
        messages: Annotated[list, add_messages]

    def respond(state):
        return {"messages": [("assistant", "Hello there!")]}
    ```

    `add_messages` is smarter than plain `add` — it can update messages by ID and handle LangChain message objects.

    **[⬆ Back to Top](#table-of-contents)**

56. ### What is MessagesState?

    `MessagesState` is a **helper class** provided by LangGraph for managing message-based conversations. It defines a state with a `messages` field (a list of message objects) and a built-in `add_messages` reducer that appends new messages. Using `MessagesState` simplifies setup for chat agents because you get typical message management without writing your own reducers.

    ```python
    from langgraph.graph import MessagesState, StateGraph

    # MessagesState already has: messages: Annotated[list, add_messages]
    class State(MessagesState):
        # extend with extra fields if needed
        user_id: str

    builder = StateGraph(State)
    ```

    **[⬆ Back to Top](#table-of-contents)**

57. ### When would you use a custom state schema instead of MessagesState?

    Use a custom state schema when your agent needs to store **more than just a list of messages**. For instance, if you need to track search results, user preferences, flags, or intermediate computation results, a custom schema with specific fields is more appropriate. `MessagesState` is helpful for quick chat prototypes but may not be sufficient for complex applications.

    **[⬆ Back to Top](#table-of-contents)**

58. ### How do you manage conversation history in state?

    Store messages in a list field (e.g., `messages`) with an append reducer. Nodes that send or receive messages add entries to this list. You can also implement **memory pruning**: if the list grows too long, remove old entries or summarise them to keep state manageable:

    ```python
    def prune_history(state: dict) -> dict:
        msgs = state["messages"]
        if len(msgs) > 20:
            # keep system message + last 10, summarise the rest
            summary = summarize(msgs[:-10])
            return {"messages": [("system", summary)] + msgs[-10:]}
        return {}
    ```

    **[⬆ Back to Top](#table-of-contents)**

59. ### What are common mistakes in LangGraph state design?

    - Using **global variables** instead of the state.
    - **Overwriting state fields** by returning the entire state.
    - Storing **large data** in the state (which should be stored externally).
    - **Missing reducers** for list-like fields, leading to lost updates.
    - Forgetting to **update the state schema** when adding new fields.

    Designing the state carefully avoids these pitfalls.

    **[⬆ Back to Top](#table-of-contents)**

60. ### How do you keep state small and efficient?

    Only store **essential information**. Summarise or compress long conversation histories. Remove or archive old data when no longer needed. Use **external storage** for large documents and store references (IDs) in the state. When using persistent memory, store only identifiers to look up data on demand. Keeping state lean improves performance and reduces storage costs.

    **[⬆ Back to Top](#table-of-contents)**


## Nodes & Best Practices

61. ### What makes a good LangGraph node?

    A good node is **single-purpose, idempotent, and side-effect aware**. It should accept the current state and return only the updates it intends to make. Nodes should avoid mutating the input state, be deterministic given the same inputs (unless intentionally nondeterministic), and handle errors gracefully. This makes nodes easier to test and reason about.

    **[⬆ Back to Top](#table-of-contents)**

62. ### Should nodes be small or large in LangGraph?

    Prefer **small, focused nodes** over monolithic ones. Small nodes make the graph structure clearer, encourage reuse, and simplify testing. However, each node call adds overhead, so extremely fine-grained decomposition may hurt performance. Strive for a **balance**: group closely related logic into one node and separate distinct steps into different nodes.

    **[⬆ Back to Top](#table-of-contents)**

63. ### How do you separate business logic from graph orchestration?

    Keep your **business logic** (tool calls, LLM prompts, data processing) inside nodes or separate functions. The **graph defines the order and conditions** of these nodes. This separation keeps orchestration declarative and easy to understand, while complex logic can be isolated and tested independently. Avoid embedding heavy logic inside routing functions; instead, use routing functions to choose between nodes that encapsulate business logic.

    ```python
    # Business logic isolated in a plain function
    def calculate_risk(transaction: dict) -> float:
        return transaction["amount"] / transaction["limit"]

    # Node wraps it for the graph
    def risk_node(state: dict) -> dict:
        return {"risk": calculate_risk(state["transaction"])}
    ```

    **[⬆ Back to Top](#table-of-contents)**

64. ### Can a node call an LLM?

    **Yes.** A node can call an LLM using LangChain models or any other library:

    ```python
    from langchain_openai import ChatOpenAI

    llm = ChatOpenAI(model="gpt-4o-mini", temperature=0.7)

    def plan_action(state: dict) -> dict:
        prompt = f"Given the goal '{state['goal']}', decide the next action."
        response = llm.invoke(prompt)
        return {"action_plan": response.content}
    ```

    LLM calls within nodes are common when building agents, such as planning or summarisation nodes.

    **[⬆ Back to Top](#table-of-contents)**

65. ### Can a node call an external API?

    **Absolutely.** Nodes can call any external API or Python library — query a web service, read/write a database, or integrate a third-party tool. Be mindful of long latency and errors; wrap API calls in `try/except` blocks and consider asynchronous execution or retries.

    ```python
    import httpx

    def fetch_weather(state: dict) -> dict:
        try:
            r = httpx.get(f"https://api.weather.com/{state['city']}", timeout=5)
            r.raise_for_status()
            return {"weather": r.json()}
        except httpx.HTTPError as e:
            return {"error": str(e)}
    ```

    **[⬆ Back to Top](#table-of-contents)**

66. ### Can a node call another graph?

    **Yes.** You can compile a subgraph and call it from within a node in a parent graph. The subgraph has its own state; you pass relevant fields from the parent state to initialise it, then merge its output back into the parent state. This technique promotes **modularity and reuse**.

    ```python
    summary_graph = build_summary_graph().compile()

    def summarize_node(state: dict) -> dict:
        result = summary_graph.invoke({"text": state["document"]})
        return {"summary": result["summary"]}
    ```

    **[⬆ Back to Top](#table-of-contents)**

67. ### What should happen if a node fails?

    If a node raises an exception, graph execution **stops and the exception bubbles up** to the caller unless you catch it. In production, it is good practice to handle errors within nodes, log them, and return an error field in the state. You can also design a **fallback path**: use a conditional edge to route to an error-handling node when an error flag is set. Retry policies can automatically retry failed nodes.

    **[⬆ Back to Top](#table-of-contents)**

68. ### How do you design idempotent nodes?

    Idempotent nodes produce the **same output state given the same input state**. To achieve this: avoid generating non-deterministic results (or record randomness in the state), do not mutate global state, and handle external calls carefully (e.g., check if an API call has already been performed and reuse the result). Idempotency is important for retries: a retried node should not re-run expensive or irreversible operations.

    ```python
    def create_user(state: dict) -> dict:
        if state.get("user_created"):       # already done — skip
            return {}
        user_id = db.create_user(state["email"])
        return {"user_id": user_id, "user_created": True}
    ```

    **[⬆ Back to Top](#table-of-contents)**

69. ### Why is idempotency important in retryable workflows?

    When a node fails and is retried, the **same operation may run multiple times**. If the node performs side effects (like sending an email or creating a database entry) and is not idempotent, the side effect may happen twice. To avoid duplicates or inconsistent state, nodes should either be idempotent or **detect whether the operation has already been performed** by checking the state or an external source.

    **[⬆ Back to Top](#table-of-contents)**

70. ### How do you avoid side effects inside LangGraph nodes?

    Where possible, **separate side effects from state updates**. If a node must perform side effects, record the outcome in the state so subsequent calls know the effect already occurred. Alternatively, use a **human approval step** before performing irreversible actions. Always catch exceptions from side-effecting operations and propagate errors via the state or fallback paths.

    **[⬆ Back to Top](#table-of-contents)**


## Conditional Edges & Routing

71. ### What is a conditional edge?

    A conditional edge **routes to different target nodes based on a condition function**. The function examines the current state and returns a string (or key). A mapping dictionary then maps this key to a target node. Conditional edges enable dynamic branching logic based on model output, tool results, or other state variables.

    ```python
    def route(state: dict) -> str:
        return state["next_action"]

    builder.add_conditional_edges("planner", route, {
        "search": "search_node",
        "calculate": "calc_node",
        "finish": END,
    })
    ```

    **[⬆ Back to Top](#table-of-contents)**

72. ### How do conditional edges enable routing?

    The condition function can look at **any part of the state** and decide where to go next. For example, after a planning node, an LLM might return a tool name; the condition function reads that name and routes to the corresponding node. This makes routing **explicit and decoupled from the LLM prompt**, improving interpretability and debuggability.

    **[⬆ Back to Top](#table-of-contents)**

73. ### How do you route based on LLM output?

    Let an LLM node add a field to the state (e.g., `next_action`). Define a routing function that reads `state["next_action"]` and returns a key matching the mapping. Then call `add_conditional_edges` with this function:

    ```python
    def planner(state: dict) -> dict:
        decision = llm.invoke(f"Choose a tool for: {state['query']}").content.strip()
        return {"next_action": decision}

    def route(state: dict) -> str:
        return state["next_action"]

    builder.add_conditional_edges("planner", route,
        {"search": "search", "summarize": "summarize", "done": END})
    ```

    **[⬆ Back to Top](#table-of-contents)**

74. ### How do you route based on tool results?

    After a tool executes, update the state with a **status or result type**. A routing function reads this status and branches accordingly. For example, if a search tool finds no results, route to a fallback search; if results are found, route to summarisation:

    ```python
    def route_after_search(state: dict) -> str:
        return "summarize" if state["docs"] else "fallback_search"

    builder.add_conditional_edges("search", route_after_search,
        {"summarize": "summarize", "fallback_search": "web_search"})
    ```

    **[⬆ Back to Top](#table-of-contents)**

75. ### How do you route based on user intent?

    Detect user intent via an **LLM classification** or a rules-based approach, store the intent in the state, and route accordingly:

    ```python
    def classify(state: dict) -> dict:
        intent = llm.invoke(f"Classify intent: {state['message']}").content
        return {"intent": intent}

    def route_intent(state: dict) -> str:
        return state["intent"]

    builder.add_conditional_edges("classify", route_intent, {
        "book_flight": "flight_subgraph",
        "cancel": "cancel_subgraph",
        "faq": "faq_node",
    })
    ```

    **[⬆ Back to Top](#table-of-contents)**

76. ### What should a routing function return?

    A routing function returns a **key that maps to one of the target nodes**. The key can be any hashable type (usually a string) and must correspond exactly to one of the keys in the mapping dictionary. If the key is not in the mapping, LangGraph raises an error, so provide a default case or handle unexpected keys explicitly. A routing function can also return a **list of keys** to fan out to multiple nodes.

    **[⬆ Back to Top](#table-of-contents)**

77. ### How do you handle unknown routes?

    Include a **fallback key** in your mapping or raise an explicit error. The fallback node can log the unexpected key and terminate gracefully. This prevents the graph from crashing due to an unknown route:

    ```python
    def route(state: dict) -> str:
        action = state.get("next_action", "")
        return action if action in {"search", "answer"} else "fallback"

    builder.add_conditional_edges("planner", route,
        {"search": "search", "answer": "answer", "fallback": "fallback_node"})
    ```

    **[⬆ Back to Top](#table-of-contents)**

78. ### What is a fallback route?

    A fallback route is a **default path** taken when the routing function returns a key not matched by any other case — similar to the `else` branch in a switch statement. Use a fallback route to handle unexpected cases or errors gracefully, such as unknown tool names or invalid user inputs.

    **[⬆ Back to Top](#table-of-contents)**

79. ### How do you avoid complex routing logic becoming unmaintainable?

    **Divide large routing logic** into smaller components — separate routers for different decision layers (one for user intent, another for tool selection). Keep routing functions simple; they should usually read one or two fields and return a key. If routing depends on complex conditions, **compute the routing key in a dedicated node** (e.g., a classifier node) and leave the routing function trivial.

    **[⬆ Back to Top](#table-of-contents)**

80. ### How do you test node routing independently?

    Test the condition functions in **isolation** by feeding them sample states and verifying they return the expected keys. Also test that the mapping dictionary covers all possible keys:

    ```python
    def test_route_returns_search():
        state = {"next_action": "search"}
        assert route(state) == "search"

    def test_route_fallback():
        state = {"next_action": "unknown_action"}
        assert route(state) == "fallback"
    ```

    For end-to-end testing, run the graph with known inputs and assert it takes the correct path.

    **[⬆ Back to Top](#table-of-contents)**


## Command & Send

81. ### What is Command in LangGraph?

    `Command` is a **special object returned by a node** to control flow more dynamically. It allows a node to specify both a **state update** and a **next-node target** without using conditional edges. `Command` accepts an `update` dictionary and a `goto` string; LangGraph merges the update into the state and then jumps to the specified node.

    ```python
    from langgraph.graph import StateGraph
    from langgraph.types import Command
    from typing import Literal

    def planner(state: dict) -> Command[Literal["search", "answer"]]:
        if needs_search(state):
            return Command(update={"step": "searching"}, goto="search")
        return Command(update={"step": "answering"}, goto="answer")
    ```

    **[⬆ Back to Top](#table-of-contents)**

82. ### How is Command different from a conditional edge?

    Conditional edges route based on a key returned from a routing function and a **mapping provided at build time**. `Command` allows a node to specify the **next node directly at runtime**, bypassing the mapping. Use `Command` when the routing logic depends on data not available at graph construction time or when the possible targets vary dynamically.

    | | Conditional Edge | Command |
    | --- | --- | --- |
    | Decision location | Separate routing function | Inside the node |
    | Mapping | Required at build time | Not needed |
    | Updates state | No (routing only) | Yes (update + goto together) |
    | Best for | Static target sets | Dynamic targets |

    **[⬆ Back to Top](#table-of-contents)**

83. ### When should you use Command instead of normal routing?

    Use `Command` when the next node **cannot be determined by a simple key-to-node mapping** or when the list of possible targets is dynamic. For example, a node might decide to spawn a new branch for each document in a list. `Command` is also useful for meta-control, such as returning a `Command(goto=END)` when a termination condition is met, or navigating to a node in a **parent graph** from a subgraph.

    **[⬆ Back to Top](#table-of-contents)**

84. ### How can Command update state and route simultaneously?

    `Command` accepts an `update` dictionary and a `goto` string. When a node returns a `Command`, LangGraph **merges the update into the state and then jumps** to the node specified by `goto`. This eliminates the need for a separate node or reducer to modify the state before routing.

    ```python
    def process(state: dict) -> Command:
        result = do_work(state)
        return Command(
            update={"result": result, "status": "complete"},
            goto="finalize",
        )
    ```

    **[⬆ Back to Top](#table-of-contents)**

85. ### What is Send in LangGraph?

    `Send` allows a node to **spawn parallel branches** of execution. When a node returns a list of `Send(node_name, state)` objects, LangGraph runs the target node once for **each** `Send`, each with its own state payload. After the branches complete, their updates are merged back into the main state using reducers. `Send` enables **map-reduce style** operations.

    ```python
    from langgraph.types import Send

    def dispatch(state: dict) -> list[Send]:
        return [Send("process_doc", {"doc": d}) for d in state["docs"]]
    ```

    **[⬆ Back to Top](#table-of-contents)**

86. ### When would you use Send?

    Use `Send` when you need to **process a list of items in parallel** or fan out tasks. For example, to summarise multiple documents or run multiple API calls concurrently, have a node return a `Send` per item. Each branch runs concurrently, and their outputs are merged back into the state via reducers.

    **[⬆ Back to Top](#table-of-contents)**

87. ### How does Send support map-reduce style workflows?

    `Send` fans out execution to multiple branches (**the map phase**), and reducers merge the partial results back into the state (**the reduce phase**). For example, a `process_doc` node extracts keywords from each document and returns `{"keywords": extracted}`. A reducer on `keywords` concatenates or deduplicates them. After all branches finish, you have a combined list across all documents.

    ```python
    from typing import Annotated, TypedDict
    from operator import add

    class State(TypedDict):
        docs: list[str]
        summaries: Annotated[list[str], add]   # reduce phase

    def process_doc(state: dict) -> dict:       # map phase
        return {"summaries": [summarize(state["doc"])]}
    ```

    **[⬆ Back to Top](#table-of-contents)**

88. ### How do you dynamically create parallel branches in LangGraph?

    Inside a node, **inspect the state** to determine how many branches are needed, then return a list of `Send` objects:

    ```python
    from langgraph.types import Send

    def dispatch(state: dict) -> list[Send]:
        docs = state["docs"]
        return [Send("process_doc", {"doc": d}) for d in docs]

    builder.add_conditional_edges("dispatch", dispatch, ["process_doc"])
    ```

    LangGraph runs `process_doc` once per document. Define reducers to merge the results back into the state.

    **[⬆ Back to Top](#table-of-contents)**

89. ### How do you aggregate results from multiple dynamically spawned tasks?

    Define **reducers for the fields** that the tasks update. Each branch might return `{"summaries": [summary], "keywords": [kw1, kw2]}`. A reducer for `summaries` appends lists, and a reducer for `keywords` combines and deduplicates. After all branches complete, the main state holds the aggregated results.

    ```python
    def dedup(old: list, new: list) -> list:
        return list(dict.fromkeys(old + new))

    class State(TypedDict):
        summaries: Annotated[list, add]
        keywords: Annotated[list, dedup]
    ```

    **[⬆ Back to Top](#table-of-contents)**

90. ### What are common use cases for dynamic parallelism?

    Common use cases include **processing multiple documents or web pages, generating multiple answer variations, running independent API calls concurrently, and splitting a dataset for map-reduce**. Parallelising tasks reduces latency and simplifies code compared to sequential loops.

    **[⬆ Back to Top](#table-of-contents)**

91. ### How would you process multiple documents in parallel using LangGraph?

    Assume `state["docs"]` holds a list of documents. Implement a `dispatch` node that returns a `Send` per document targeting a `process_doc` node. Each branch summarises one document and returns `{"summaries": [summary]}`. Register an append reducer for `summaries`:

    ```python
    from langgraph.graph import StateGraph, START, END
    from langgraph.types import Send
    from typing import Annotated, TypedDict
    from operator import add

    class State(TypedDict):
        docs: list[str]
        summaries: Annotated[list[str], add]

    def dispatch(state): 
        return [Send("process_doc", {"doc": d}) for d in state["docs"]]

    def process_doc(state):
        return {"summaries": [f"summary of: {state['doc'][:20]}"]}

    b = StateGraph(State)
    b.add_node("process_doc", process_doc)
    b.add_conditional_edges(START, dispatch, ["process_doc"])
    b.add_edge("process_doc", END)
    graph = b.compile()
    ```

    **[⬆ Back to Top](#table-of-contents)**

92. ### How would you fan out tasks and fan in results?

    Use `Send` to **fan out** tasks — each branch runs independently on a portion of the input. Define **reducers to fan in** results by combining updates from each branch. This pattern is analogous to map-reduce: map each input to an output, then reduce outputs into a single result. LangGraph handles concurrency and merging, so you only implement the node logic and reducers.

    **[⬆ Back to Top](#table-of-contents)**

93. ### How do reducers help with Send-based workflows?

    Reducers **combine updates from parallel branches**. Without reducers, the last branch's update would overwrite previous ones, leading to data loss. For example, if each branch returns `{"sum": value}`, a reducer can sum these values to produce a total. Reducers ensure parallel results are merged in a well-defined way.

    ```python
    class State(TypedDict):
        total: Annotated[int, lambda old, new: old + new]
    ```

    **[⬆ Back to Top](#table-of-contents)**

94. ### What can go wrong when multiple branches update the same state?

    If you **forget to define a reducer** for a key updated by multiple branches, the last update overwrites earlier ones, **losing data**. Conflicting updates with no clear merge strategy produce inconsistent results. Also, if branches depend on mutable shared state **outside** the LangGraph state, you may hit race conditions. Always design state updates and reducers carefully for parallel workflows.

    **[⬆ Back to Top](#table-of-contents)**

95. ### How do you control the number of dynamic tasks created?

    Inspect the input in your dispatch node and **limit the number of branches**. For a large dataset, batch documents into groups of a fixed size and send each batch to a branch. Alternatively, skip items already processed. There is no built-in throttle, so controlling fan-out is your responsibility:

    ```python
    def dispatch(state: dict) -> list[Send]:
        docs = state["docs"][:50]            # cap at 50 branches
        batches = [docs[i:i+10] for i in range(0, len(docs), 10)]
        return [Send("process_batch", {"batch": b}) for b in batches]
    ```

    **[⬆ Back to Top](#table-of-contents)**

96. ### How do you prevent excessive parallel execution?

    To avoid overwhelming resources, **limit the number of branches** you spawn or implement concurrency control outside LangGraph (e.g., `asyncio.Semaphore` or a worker queue). You can also chunk data into manageable sizes. LangGraph itself does not provide built-in rate limiting for `Send`, so consider a custom node that applies backpressure or splits tasks across multiple invocations.

    **[⬆ Back to Top](#table-of-contents)**

97. ### How do you design a graph for batch processing?

    In batch processing, you iterate over items and aggregate results. Use `Send` to process items in parallel with a reducer to combine results. Then route to a **final node** that post-processes aggregated results. Provide a termination condition: after processing all items, route to `END`. Optionally include error handling to skip or retry failed items.

    **[⬆ Back to Top](#table-of-contents)**

98. ### How do you design a graph for multi-step document analysis?

    Define **separate nodes for each step** (extract facts, classify topics, summarise). Use a dispatch node to spawn parallel branches for each document, then sequentially call each processing node within the branch. Finally, use reducers to combine results across documents. This modular design improves maintainability and lets you reuse nodes across workflows.

    **[⬆ Back to Top](#table-of-contents)**

99. ### How do you design a graph that routes dynamically at runtime?

    Use **conditional edges or `Command`** to decide the next node based on the state. If the set of possible targets is known at build time, conditional edges with a mapping suffice. If targets are dynamic or depend on external data, return a `Command` specifying the next node. Keep routing logic simple and base it on a small number of state variables.

    **[⬆ Back to Top](#table-of-contents)**

100. ### How do Command and Send improve graph flexibility?

     `Command` allows nodes to **dynamically choose the next node and update state simultaneously**. `Send` enables **dynamic parallelism** by spawning multiple branches. Together they let your graph adapt its control flow at runtime, handle variable numbers of tasks, and perform complex operations without bloating the graph definition.

     **[⬆ Back to Top](#table-of-contents)**


## Agents & Tool Calling

101. ### What is an agent in LangGraph?

     An agent is a system that uses an **LLM (and tools)** to reason about tasks, select actions, and maintain conversation state. In LangGraph, you build an agent by defining nodes for planning, tool execution, checking termination, and memory updates. The agent **loops until a termination condition** is met, returning the final answer or taking a fallback path. Agents can call tools, search the web, interact with humans, and maintain long-term memory.

     **[⬆ Back to Top](#table-of-contents)**

102. ### How do you build a ReAct-style agent in LangGraph?

     The **ReAct pattern** alternates between **reasoning** (LLM deciding the next tool) and **acting** (executing the tool). LangGraph ships a prebuilt helper, but you can also build it manually:

     ```python
     from langgraph.prebuilt import create_react_agent
     from langchain_openai import ChatOpenAI
     from langchain_core.tools import tool

     @tool
     def search(query: str) -> str:
         """Search the web for a query."""
         return f"results for {query}"

     llm = ChatOpenAI(model="gpt-4o-mini")
     agent = create_react_agent(llm, tools=[search])

     result = agent.invoke({"messages": [("user", "Find news on AI")]})
     ```

     Manually, you implement a `planner` node that uses the LLM to pick the next action, a conditional edge that routes to the tool node, and a loop back to the planner until a termination signal.

     **[⬆ Back to Top](#table-of-contents)**

103. ### What is the difference between a workflow and an agent?

     A **workflow** is a predefined sequence of operations with deterministic logic. An **agent** incorporates reasoning and decision-making, often via an LLM, to determine its next actions. In LangGraph, workflows can be static graphs, whereas agents typically involve **cycles and dynamic routing**. Agents also maintain conversation history and may interact with humans or external systems.

     **[⬆ Back to Top](#table-of-contents)**

104. ### How do you design an agent loop in LangGraph?

     Implement a `planner` node that uses an LLM to decide the next action and updates the state with an action field. Add a conditional edge (or `Command`) to route to the corresponding tool node or to `END`. After the tool node executes, update the state with the result and route **back to the planner**. This forms a loop. Add a reducer to accumulate messages or logs:

     ```python
     def should_continue(state: dict) -> str:
         return "end" if state.get("is_done") else "tool"

     builder.add_node("planner", planner)
     builder.add_node("tool", tool_node)
     builder.add_edge(START, "planner")
     builder.add_conditional_edges("planner", should_continue,
         {"tool": "tool", "end": END})
     builder.add_edge("tool", "planner")   # loop
     ```

     **[⬆ Back to Top](#table-of-contents)**

105. ### How do you decide when an agent should stop?

     Strategies include: the planner returns a special action (e.g., `"final"`) indicating completion; a **termination node checks a flag** (e.g., `is_done`) and routes to `END`; a **maximum iteration count** prevents infinite loops; or a **human approval node** decides to stop. Choose based on your agent's design and risk tolerance.

     **[⬆ Back to Top](#table-of-contents)**

106. ### How do you prevent an agent from looping forever?

     Use **explicit termination conditions**. Include a counter in the state, increment it each loop, and route to a fail-safe node or `END` when it exceeds a threshold. Alternatively, check an `is_done` flag from the planner. The `recursion_limit` config also acts as a hard safety net:

     ```python
     def planner(state: dict) -> dict:
         count = state.get("iterations", 0) + 1
         if count > 10:
             return {"is_done": True, "iterations": count}
         # ... normal planning
         return {"iterations": count, "next_action": decide(state)}
     ```

     **[⬆ Back to Top](#table-of-contents)**

107. ### What is the role of the LLM node in an agent graph?

     The LLM node is responsible for **reasoning about the current conversation and deciding the next action**. It might generate thoughts (for logging), choose a tool, or summarise intermediate results. The LLM's output guides control flow via conditional edges or `Command`. Because LLMs are nondeterministic, reproducible behaviour requires controlling randomness (e.g., `temperature=0`) and handling errors gracefully.

     **[⬆ Back to Top](#table-of-contents)**

108. ### What is the role of the tool execution node?

     The tool execution node **calls an external tool** with arguments generated by the planner. It returns a partial state update containing the tool's output (e.g., `{"tool_result": result}`) and possibly appends a message summarising the call. After the tool node finishes, control typically returns to the planner so the agent can decide the next action. LangGraph's prebuilt `ToolNode` automates much of this:

     ```python
     from langgraph.prebuilt import ToolNode
     tool_node = ToolNode([search, calculator])
     builder.add_node("tools", tool_node)
     ```

     **[⬆ Back to Top](#table-of-contents)**

109. ### How does an agent decide which tool to call?

     The planner node uses an **LLM to generate a tool name and arguments** (often via the model's native function-calling/tool-calling API). The agent then uses a conditional edge or `Command` to route to the corresponding tool node. Available tools are defined up front and may include search, calculator, code execution, web scraping, etc. Tool metadata (descriptions, schemas) is passed to the LLM so it can choose appropriately.

     ```python
     llm_with_tools = llm.bind_tools([search, calculator])

     def planner(state: dict) -> dict:
         response = llm_with_tools.invoke(state["messages"])
         return {"messages": [response]}  # response may contain tool_calls
     ```

     **[⬆ Back to Top](#table-of-contents)**

110. ### How do you handle invalid tool calls?

     **Validate tool names and arguments** before executing a tool. If the planner returns an unknown tool or invalid arguments, route to an error-handling node. The error node can notify the user, log the error, and let the planner try again. You can also include "self-check" prompts asking the LLM to validate its own tool output.

     ```python
     ALLOWED = {"search", "calculator"}

     def validate(state: dict) -> str:
         call = state["messages"][-1].tool_calls[0]
         return "execute" if call["name"] in ALLOWED else "error"
     ```

     **[⬆ Back to Top](#table-of-contents)**

111. ### How do you handle tool execution errors?

     **Wrap tool calls in try/except** blocks. On exception, update the state with an error field and set a flag (e.g., `state["error"] = True`). Use conditional edges or `Command` to route to an error-handling node. Log the exception, and optionally implement retry logic with exponential backoff. If a tool fails repeatedly, inform the user and abort gracefully:

     ```python
     def tool_node(state: dict) -> dict:
         try:
             result = run_tool(state["tool_name"], state["tool_args"])
             return {"tool_result": result, "error": None}
         except Exception as e:
             return {"error": str(e)}
     ```

     **[⬆ Back to Top](#table-of-contents)**

112. ### How do you return tool results back to the LLM?

     After executing a tool, **update the state with the tool result** and append a message describing it. Then route back to the planner, which reads the result and incorporates it into its next prompt. Optionally summarise long tool outputs before including them to avoid exceeding the context window:

     ```python
     from langchain_core.messages import ToolMessage

     def tool_node(state: dict) -> dict:
         call = state["messages"][-1].tool_calls[0]
         result = run_tool(call["name"], call["args"])
         return {"messages": [ToolMessage(content=str(result),
                                          tool_call_id=call["id"])]}
     ```

     **[⬆ Back to Top](#table-of-contents)**

113. ### What is the difference between tool calling and function calling?

     **Tool calling** often refers to the ReAct pattern where the LLM chooses a tool by name and arguments, sometimes via free-text parsing. **Function calling** is a specific feature of some LLM APIs where the model returns a **structured JSON object** specifying the function name and arguments. Both work in LangGraph. Tool calling may require custom output parsing, while function calling provides structured output natively. In either case, the graph must route to the correct function and return results in the state.

     **[⬆ Back to Top](#table-of-contents)**

114. ### How do you add multiple tools to a LangGraph agent?

     Define **separate functions for each tool** (or use `@tool`), bind them to the LLM, and use a `ToolNode` to dispatch:

     ```python
     from langchain_core.tools import tool
     from langgraph.prebuilt import ToolNode

     @tool
     def get_weather(city: str) -> str:
         """Get the weather for a city."""
         return f"Sunny in {city}"

     @tool
     def get_time(tz: str) -> str:
         """Get the current time in a timezone."""
         return "12:00 PM"

     tools = [get_weather, get_time]
     llm_with_tools = llm.bind_tools(tools)
     tool_node = ToolNode(tools)   # routes by tool name automatically
     ```

     **[⬆ Back to Top](#table-of-contents)**

115. ### How do you restrict which tools an agent can use?

     Only include the **names and descriptions of allowed tools** in the planner prompt / `bind_tools` call. Validate the returned tool name against the allowed list; if not allowed, route to an error node. Add guardrails in the prompt, such as "Do not call tools that are not in the provided list." Restricting tools reduces the risk of unintended actions.

     **[⬆ Back to Top](#table-of-contents)**

116. ### How do you design a safe tool-calling agent?

     Combine **validation, guardrails, and monitoring**. Use structured outputs (function calling) where possible. Validate tool inputs and check they are within allowed ranges. Provide clear instructions about not performing sensitive actions without confirmation. Implement a **human approval node** for high-impact actions. Log all tool calls for audit and include fallback paths for unanticipated scenarios.

     **[⬆ Back to Top](#table-of-contents)**

117. ### How do you validate tool input before execution?

     Use **JSON schemas or Pydantic models** to parse and validate tool arguments returned by the LLM. If validation fails, return an error field and route to an error node. Optionally ask the LLM to self-validate its output against the schema. Always sanitise user input and LLM-generated arguments before passing them to external systems:

     ```python
     from pydantic import BaseModel, ValidationError

     class TransferArgs(BaseModel):
         account: str
         amount: float

     def validate_node(state: dict) -> dict:
         try:
             args = TransferArgs(**state["tool_args"])
             return {"validated_args": args.model_dump()}
         except ValidationError as e:
             return {"error": str(e)}
     ```

     **[⬆ Back to Top](#table-of-contents)**

118. ### How do you handle tools with side effects?

     For tools that modify external systems (sending emails, updating databases), implement a **preview/approval step**. The agent composes the action and displays it to the user for confirmation. After approval, the tool executes and records the outcome in the state. Alternatively, implement transaction-like logic: check if the side effect already occurred to avoid duplicates, and record the effect in state. Tools with side effects should have **additional guardrails and logging**.

     **[⬆ Back to Top](#table-of-contents)**

119. ### How do you design an agent for customer support?

     Define a state schema with **conversation history, user info, ticket details, and flags**. Implement nodes for intent classification, knowledge-base lookup, summarisation, and ticket creation. A planner node chooses the action (answer from FAQ, create ticket, transfer to human). A routing function directs to the relevant node. Include a **human approval node** for escalations. Persist long-term user preferences in a store for personalisation.

     ```python
     class SupportState(MessagesState):
         user_id: str
         intent: str
         ticket_id: str | None
         escalate: bool
     ```

     **[⬆ Back to Top](#table-of-contents)**

120. ### How do you design an agent for code generation?

     Define nodes for **understanding the problem, planning components, generating code, and executing/testing** it. Use state fields to store partial code, test results, and error messages. **Loop between generation and testing** until tests pass or a limit is reached. Optionally include a node to refactor or document the code. Handle execution errors and avoid running untrusted code in unsafe environments (use a sandbox):

     ```python
     def route_after_test(state: dict) -> str:
         if state["tests_passed"]:
             return "done"
         return "regenerate" if state["attempts"] < 5 else "give_up"
     ```

     **[⬆ Back to Top](#table-of-contents)**


## Persistence & Checkpointing

121. ### What is checkpointing in LangGraph?

     Checkpointing refers to **persisting the state of a graph at specific points** so execution can resume later. LangGraph uses **checkpointers** to save snapshots of the state for each thread (after every super-step). This enables pausing and resuming conversations, replaying previous steps, and recovering after a crash.

     ```python
     from langgraph.checkpoint.memory import MemorySaver

     checkpointer = MemorySaver()
     graph = builder.compile(checkpointer=checkpointer)
     config = {"configurable": {"thread_id": "conversation-1"}}
     graph.invoke({"messages": [("user", "hi")]}, config=config)
     ```

     **[⬆ Back to Top](#table-of-contents)**

122. ### Why are checkpointers important?

     Checkpointers provide **short-term, thread-scoped memory**. Without them, the state would exist only in memory, and if the process terminated or timed out, the context would be lost. Checkpointers store state in durable storage so a conversation can **resume exactly where it left off** — essential for multi-turn chat, human-in-the-loop, and fault recovery.

     **[⬆ Back to Top](#table-of-contents)**

123. ### What information is stored in a checkpoint?

     A checkpoint stores the **current state**, metadata about the graph (node pointers, thread ID, version, and which node runs next), and possibly the message that triggered an interrupt. Checkpoints capture the **state and graph context needed to resume** execution from the exact point of suspension.

     **[⬆ Back to Top](#table-of-contents)**

124. ### What is a thread in LangGraph?

     A **thread** represents a single conversation or execution of a graph. Each thread has a unique identifier (`thread_id`) and its own checkpoint history. When running multiple conversations concurrently, each thread's state and checkpoints are kept **separate**, so they never mix.

     **[⬆ Back to Top](#table-of-contents)**

125. ### What is thread_id used for?

     `thread_id` **identifies which conversation or execution** you want to resume. When you call `invoke()` or `stream()`, you pass `thread_id` in the config to associate the execution with stored state. It allows the system to maintain multiple concurrent conversations without mixing their states:

     ```python
     config = {"configurable": {"thread_id": "user-42-session-1"}}
     graph.invoke(input_state, config=config)
     ```

     **[⬆ Back to Top](#table-of-contents)**

126. ### How does LangGraph resume execution from a checkpoint?

     When you call `invoke()` or `stream()` with a `thread_id` that has an existing checkpoint, LangGraph **loads the saved state and graph context**, then resumes from the next node after the checkpointed node. If the previous execution was interrupted, LangGraph expects a human input or resume command before continuing.

     ```python
     # First call runs and checkpoints
     graph.invoke({"messages": [("user", "hi")]}, config)
     # Later call with same thread_id resumes with prior context
     graph.invoke({"messages": [("user", "continue")]}, config)
     ```

     **[⬆ Back to Top](#table-of-contents)**

127. ### What is the difference between short-term memory and checkpointed state?

     **Short-term memory** is the state within a conversation that persists across nodes but not across sessions unless checkpointed. The **checkpointed state** is persisted across sessions using a checkpointer. Without persistence, state exists only in memory during a single function call. In practice, checkpointed state *is* how LangGraph implements durable short-term memory for a thread.

     **[⬆ Back to Top](#table-of-contents)**

128. ### How do you persist conversation state across user sessions?

     Configure a **durable checkpointer** (Postgres, Redis, SQLite) when compiling, and provide a stable `thread_id` per user/conversation. After each node, LangGraph stores the updated state under that thread ID. When the user returns, call `invoke()` again with the same `thread_id` to load state and resume:

     ```python
     from langgraph.checkpoint.postgres import PostgresSaver

     with PostgresSaver.from_conn_string("postgresql://...") as cp:
         graph = builder.compile(checkpointer=cp)
         graph.invoke(state, {"configurable": {"thread_id": "user-42"}})
     ```

     **[⬆ Back to Top](#table-of-contents)**

129. ### What happens if no checkpointer is configured?

     Without a checkpointer, the state is held **in memory only for the duration of the call**. Once the call completes or the process terminates, the state is lost. Features like **human-in-the-loop pauses and cross-session memory cannot be supported** without checkpointing.

     **[⬆ Back to Top](#table-of-contents)**

130. ### How do checkpointers support fault tolerance?

     If your process **crashes or times out**, you can restart it and **resume graph execution from the last checkpoint**. Because the state and graph context are stored durably, the agent does not lose progress and avoids repeating completed work.

     **[⬆ Back to Top](#table-of-contents)**

131. ### How do checkpointers support human-in-the-loop workflows?

     When you call `interrupt()`, LangGraph **stores the current state** and sets the thread status to interrupted. The system waits for human input. The human sends a resume command (via `Command(resume=...)`) with updated data. LangGraph **loads the checkpointed state and continues** execution from the interrupt point. Without checkpointing, this pause/resume cycle is impossible.

     **[⬆ Back to Top](#table-of-contents)**

132. ### What are common checkpoint backends?

     | Backend | Use Case |
     | --- | --- |
     | **In-memory (`MemorySaver`)** | Local development, tests |
     | **SQLite (`SqliteSaver`)** | Single-node, lightweight persistence |
     | **PostgreSQL (`PostgresSaver`)** | Production, durable, transactional |
     | **Redis** | Distributed, low-latency, TTL support |

     You can also implement **custom checkpointers** to meet specific persistence needs.

     **[⬆ Back to Top](#table-of-contents)**

133. ### When would you use an in-memory checkpointer?

     Use an **in-memory checkpointer (`MemorySaver`)** for local development and unit tests. It is fast and easy to set up but does **not persist data across process restarts**. It is ideal for testing human-in-the-loop or multi-turn logic without standing up a database.

     **[⬆ Back to Top](#table-of-contents)**

134. ### Why is an in-memory checkpointer not suitable for production?

     An in-memory checkpointer stores state in the **application process's memory**. If the process crashes or is scaled down, the state is lost. High-availability systems require **durable storage** (Redis or a database) to persist state across restarts and to share state across multiple workers.

     **[⬆ Back to Top](#table-of-contents)**

135. ### How would you use PostgreSQL or Redis for checkpointing?

     Instantiate a Postgres or Redis checkpointer with connection parameters and pass it to `compile()`. LangGraph saves state snapshots to that backend:

     ```python
     from langgraph.checkpoint.postgres import PostgresSaver

     DB_URI = "postgresql://user:pass@localhost:5432/langgraph"
     with PostgresSaver.from_conn_string(DB_URI) as checkpointer:
         checkpointer.setup()                  # creates tables on first run
         graph = builder.compile(checkpointer=checkpointer)
         graph.invoke(state, {"configurable": {"thread_id": "t1"}})
     ```

     For Redis, use the Redis checkpointer package and configure a connection URL and optional key prefix/TTL.

     **[⬆ Back to Top](#table-of-contents)**

136. ### How do you manage checkpoint storage growth?

     Periodically **clean up or archive older checkpoints**. Implement retention policies: keep only the most recent checkpoints per thread, or delete checkpoints after a certain age. Use **TTL in Redis** or scheduled jobs in your database to purge old rows. Monitor table/key growth to avoid unbounded storage costs.

     **[⬆ Back to Top](#table-of-contents)**

137. ### How do you clean up old checkpoints?

     If using **Redis**, configure a TTL so keys expire automatically. If using a **database**, run a scheduled query to delete old rows (e.g., older than 30 days). You can also build a background worker that deletes checkpoints beyond a retention window:

     ```sql
     DELETE FROM checkpoints
     WHERE created_at < NOW() - INTERVAL '30 days';
     ```

     **[⬆ Back to Top](#table-of-contents)**

138. ### How do you handle checkpoint schema changes?

     If you change the state schema, ensure your code can **handle checkpoints with older schemas**. Use **default values for missing fields** and ignore unknown fields. Write migration scripts where necessary, or start fresh threads for the new version. Graceful handling of old checkpoints prevents crashes when deploying schema changes.

     **[⬆ Back to Top](#table-of-contents)**

139. ### How do you version graph state?

     Include a **`version` field** in the state or checkpoint metadata. When loading a checkpoint, check the version and apply migrations if needed. If a checkpoint version does not match the current graph version, either migrate the state or start a new thread. Versioning makes upgrades safe and traceable.

     **[⬆ Back to Top](#table-of-contents)**

140. ### How do you debug state using checkpoints?

     **Load the stored state** from your checkpointer and inspect it. Use `get_state()` and `get_state_history()` to view current and past snapshots. Compare state at different checkpoints to see how it evolved. When an error occurs, examine the state and node pointer to understand what happened:

     ```python
     snapshot = graph.get_state(config)
     print(snapshot.values)        # current state
     for past in graph.get_state_history(config):
         print(past.next, past.values)   # step-by-step history
     ```

     **[⬆ Back to Top](#table-of-contents)**


## Memory

141. ### What is memory in LangGraph?

     Memory refers to **persisted information about the user or conversation** beyond the immediate context. There are two categories: **short-term memory** stored via checkpointers (thread-scoped), and **long-term memory** stored via persistent stores (cross-thread, cross-session). Memory lets agents recall preferences, facts, and past interactions.

     **[⬆ Back to Top](#table-of-contents)**

142. ### What is the difference between checkpointing and memory?

     **Checkpointing** stores the entire **state snapshot of a conversation thread**. **Memory** (via stores) typically refers to **user-specific data stored across threads or sessions**. Checkpoints capture transient conversation context; memory captures durable knowledge or preferences that should outlive any single conversation.

     **[⬆ Back to Top](#table-of-contents)**

143. ### What is short-term memory in LangGraph agents?

     Short-term memory is the **conversation state stored by checkpointers** for a given thread. It includes messages, tool outputs, and flags. It persists across a single conversation but may be discarded (or expired) after the session ends. It is scoped to one `thread_id`.

     **[⬆ Back to Top](#table-of-contents)**

144. ### What is long-term memory in LangGraph agents?

     Long-term memory is stored via **persistent stores** and holds data that should persist **across conversations or sessions**, such as user preferences, learned facts, or embeddings. It is keyed by a namespace (e.g., user ID) rather than thread, so it is available in every future conversation with that user.

     **[⬆ Back to Top](#table-of-contents)**

145. ### What is a persistent store in LangGraph?

     A **persistent store** is an abstraction for storing **key-value (and optionally vector-searchable) data** persistently. It is separate from checkpointers and used to save long-term memory for reuse in future conversations. LangGraph's `BaseStore` interface supports namespaced puts/gets and semantic search:

     ```python
     from langgraph.store.memory import InMemoryStore

     store = InMemoryStore()
     graph = builder.compile(checkpointer=cp, store=store)

     def remember(state, *, store):
         store.put(("users", state["user_id"]), "pref", {"theme": "dark"})
         return {}
     ```

     **[⬆ Back to Top](#table-of-contents)**

146. ### How do you store user preferences across sessions?

     Use a **store keyed by user ID**. When a user provides a preference, save it in the store under a namespace like `("users", user_id)`. In subsequent conversations, query the store for that user and retrieve preferences:

     ```python
     def save_pref(state, *, store):
         store.put(("users", state["user_id"]), "preferences",
                   {"language": state["language"]})
         return {}

     def load_pref(state, *, store):
         item = store.get(("users", state["user_id"]), "preferences")
         return {"preferences": item.value if item else {}}
     ```

     **[⬆ Back to Top](#table-of-contents)**

147. ### How do you retrieve relevant memory during graph execution?

     Implement a node that **queries the store** based on the user ID or context. With a vector-enabled store, you can do semantic search to fetch only the most relevant memories. The retrieved memory is added to the state for use by subsequent nodes:

     ```python
     def recall(state, *, store):
         results = store.search(("memories", state["user_id"]),
                                query=state["question"], limit=3)
         return {"relevant_memories": [r.value for r in results]}
     ```

     **[⬆ Back to Top](#table-of-contents)**

148. ### How do you prevent memory from becoming noisy?

     Store **structured data** and set retention policies. **Filter memory retrieval** to fetch only information relevant to the current task (e.g., via semantic search with a limit). Summarise or compress past conversations to reduce noise. Regularly review and clean up the store to remove stale or low-value entries.

     **[⬆ Back to Top](#table-of-contents)**

149. ### How do you decide what information should be saved to memory?

     Save information that will be **relevant to future tasks or personalisation** — preferences, recurring facts, important decisions. Do **not save transient or sensitive information** unless required. Evaluate memory usage regularly and prune data unlikely to be reused. A common pattern is to use an LLM to extract durable facts worth saving from each conversation.

     **[⬆ Back to Top](#table-of-contents)**

150. ### How do you delete or update stored memory?

     Use the **store's API** to remove or update entries (`store.put` to overwrite, `store.delete` to remove). Provide **user-facing commands** to manage their data (e.g., "forget my preferences"). Implement retention policies to automatically expire old entries:

     ```python
     def forget(state, *, store):
         store.delete(("users", state["user_id"]), "preferences")
         return {"message": "Your preferences have been cleared."}
     ```

     **[⬆ Back to Top](#table-of-contents)**

151. ### How do you design memory for a personal assistant agent?

     Maintain a **store keyed by user ID** holding preferences, contacts, and previous conversation summaries. Query this store at the **start of a session** to personalise responses. Update the store when the user provides new information, and allow the user to manage stored data. Combine with semantic search so the assistant recalls only contextually relevant memories.

     **[⬆ Back to Top](#table-of-contents)**

152. ### How do you design memory for enterprise support agents?

     Enterprise agents may need to remember **customer purchase history, tickets, and account information**. Use a **secure, centralised store** with access controls. Retrieve relevant ticket history or product info at the start of a conversation. Save new interactions for future reference and **comply with data-protection regulations** (GDPR, CCPA). Separate per-customer namespaces to prevent data leakage.

     **[⬆ Back to Top](#table-of-contents)**

153. ### How do you handle sensitive data in memory?

     **Encrypt sensitive data** at rest and in transit. Implement access controls and audit logging. Only store necessary data and **anonymise** where possible. Provide users options to view, edit, and delete their data. Comply with privacy regulations such as GDPR and CCPA. Consider field-level encryption for particularly sensitive fields like payment details.

     **[⬆ Back to Top](#table-of-contents)**

154. ### How do you separate user-specific memory from global memory?

     Use **separate namespaces or key prefixes** in the store. Prefix user-specific keys with the user ID (e.g., `("users", user_id)`) to avoid collisions, and keep **global knowledge** in a distinct namespace (e.g., `("global", "policies")`). This separation prevents one user's data from leaking into another's context.

     **[⬆ Back to Top](#table-of-contents)**

155. ### How do you test memory behaviour in LangGraph?

     Write **unit tests** that insert data into the store, invoke the graph, and verify the data is retrieved and used correctly. Simulate scenarios where memory is missing or outdated and ensure the agent handles them gracefully:

     ```python
     def test_recall_preferences():
         store = InMemoryStore()
         store.put(("users", "u1"), "preferences", {"lang": "fr"})
         graph = build_graph().compile(store=store)
         out = graph.invoke({"user_id": "u1", "question": "hi"})
         assert out["preferences"]["lang"] == "fr"
     ```

     **[⬆ Back to Top](#table-of-contents)**


## Human-in-the-Loop

156. ### What is human-in-the-loop execution in LangGraph?

     Human-in-the-loop (HITL) allows a **human to pause, review, or modify the agent's behaviour** at certain points. You call `interrupt()` to pause execution before or after a node. Execution remains suspended (state saved via checkpointer) until a human provides input to resume. This is essential for approval workflows, content review, and safety gating.

     **[⬆ Back to Top](#table-of-contents)**

157. ### What is an interrupt in LangGraph?

     `interrupt()` is a function that **pauses graph execution and stores the current state** in the checkpointer. It surfaces a payload (e.g., a question or draft) to the caller and marks the thread as interrupted. Execution resumes when you invoke the graph again with a `Command(resume=value)`:

     ```python
     from langgraph.types import interrupt, Command

     def review_node(state: dict) -> dict:
         decision = interrupt({"draft": state["draft"]})  # pauses here
         return {"approved": decision == "approve"}

     # Resume from the client:
     graph.invoke(Command(resume="approve"), config)
     ```

     **[⬆ Back to Top](#table-of-contents)**

158. ### When would you interrupt before a node?

     Interrupt **before a node** when you need human approval **before executing** the node's logic. For example, before sending an email or executing a financial transaction, interrupt and ask the user to review the draft or confirm the action. This prevents irreversible side effects from occurring without consent.

     **[⬆ Back to Top](#table-of-contents)**

159. ### When would you interrupt after a node?

     Interrupt **after a node** when you need human feedback on the node's **output**. For example, after summarising a document or generating code, you may want a human to verify the result before proceeding to the next step. This is useful for quality control gates.

     **[⬆ Back to Top](#table-of-contents)**

160. ### How do you resume a graph after human approval?

     When a graph is interrupted, LangGraph stores the state and the interrupt payload. The human provides a **resume value** via `Command(resume=...)`. LangGraph injects that value as the return of `interrupt()` and continues execution from that point:

     ```python
     # The interrupt() call returns the resume value
     graph.invoke(Command(resume={"approved": True}),
                  config={"configurable": {"thread_id": "t1"}})
     ```

     **[⬆ Back to Top](#table-of-contents)**

161. ### How do you design an approval workflow in LangGraph?

     An approval workflow **pauses at critical points for human review**. Package all relevant context (draft, transaction) into the state before the pause, call `interrupt()`, and use the resume value to decide whether to proceed. Include a boolean flag (e.g., `approved`) and check it in routing:

     ```python
     from langgraph.graph import StateGraph, START, END
     from langgraph.types import interrupt
     from typing import TypedDict

     class ApprovalState(TypedDict):
         draft: str
         approved: bool
         result: str

     def prepare(state): return {"draft": "Hello, this is your draft.", "approved": False}

     def wait(state):
         decision = interrupt({"draft": state["draft"], "prompt": "Approve?"})
         return {"approved": decision == "approve"}

     def send(state):
         return {"result": "sent" if state["approved"] else "rejected"}

     b = StateGraph(ApprovalState)
     b.add_node("prepare", prepare); b.add_node("wait", wait); b.add_node("send", send)
     b.add_edge(START, "prepare"); b.add_edge("prepare", "wait")
     b.add_edge("wait", "send"); b.add_edge("send", END)
     app = b.compile(checkpointer=MemorySaver())
     ```

     **[⬆ Back to Top](#table-of-contents)**

162. ### How do you allow a human to edit state before resuming?

     When you interrupt, LangGraph persists the state. Expose a **UI that displays the current state** and permits changes. After editing, the UI sends a resume command with the updated values. In your node, treat the resume value as input and **merge it into the state** (e.g., replacing the draft text). You can also use `graph.update_state()` to apply edits directly before resuming:

     ```python
     graph.update_state(config, {"draft": "Edited draft text"})
     graph.invoke(Command(resume="approve"), config)
     ```

     **[⬆ Back to Top](#table-of-contents)**

163. ### How do you review tool calls before execution?

     Create a node that **constructs the tool call** and an `interrupt()` before executing it. The state includes the tool name and arguments. After the human confirms, the resume triggers a node that actually invokes the tool. Alternatively, a routing function can inspect tool parameters and decide whether to proceed automatically or require approval based on thresholds (e.g., transaction amount).

     **[⬆ Back to Top](#table-of-contents)**

164. ### How do you handle rejected human approval?

     If the human **rejects** the proposed action, route to an alternative node that either revises the action or terminates the workflow. For instance, if a transaction is denied, log the decision and return a message to the user. The rejection path should **clean up temporary state** (drafts) and may prompt for new input. Always ensure rejection prevents the side effect from occurring:

     ```python
     def route_decision(state: dict) -> str:
         return "execute" if state["approved"] else "handle_rejection"
     ```

     **[⬆ Back to Top](#table-of-contents)**

165. ### How do you design a graph for compliance review?

     Compliance reviews involve **strict policies and audit trails**. Use explicit interrupt points before executing actions subject to compliance (e.g., sending regulated content). Store the **review decision and reviewer identity** in the state or a dedicated audit log. Add validations to ensure required approvals are recorded before proceeding. In enterprise settings, integrate with external systems (ticketing tools) to capture the review and pass back the outcome.

     **[⬆ Back to Top](#table-of-contents)**

166. ### How do you design a graph for financial transaction approval?

     Financial transactions require **security checks and multi-party approvals**. Authenticate the user and gather transaction details. Add a node to calculate risk or perform compliance checks, then `interrupt()` for human or system approval. Use conditional edges to route transactions above certain thresholds to **additional approval nodes**. After approval, call the payment API in a node that records the outcome. Ensure state updates (like balances) occur atomically, and errors trigger rollback/compensation logic.

     **[⬆ Back to Top](#table-of-contents)**

167. ### How do you prevent unauthorized graph resumes?

     Because interrupting pauses execution awaiting a resume, you must **authenticate the resumer**. Verify that the identity matches the original thread owner or an authorised reviewer. Store a session token or user ID in the state and check it when processing the resume. If authentication fails, **deny the resume** and log the attempt. This prevents malicious parties from injecting messages into a paused workflow.

     **[⬆ Back to Top](#table-of-contents)**

168. ### How do interrupts depend on checkpointing?

     Interrupts **rely on checkpoints** to persist the state and graph context. When you call `interrupt()`, LangGraph serialises the current state and node pointer into the checkpointer. Without checkpointing, the state would be lost when the process pauses. The ability to resume later is therefore **tied to having a configured checkpointer** (in-memory for tests, durable storage for production). If you disable checkpointing, interrupts will not work.

     **[⬆ Back to Top](#table-of-contents)**

169. ### How do you audit human decisions in LangGraph?

     Record metadata such as **reviewer identity, timestamps, decision values, and comments**. Add an `audit_log` list to the state and append an entry whenever an approval node executes:

     ```python
     from datetime import datetime, timezone

     def record_approval(state: dict) -> dict:
         entry = {
             "reviewer": state["current_user"],
             "decision": state["approved"],
             "timestamp": datetime.now(timezone.utc).isoformat(),
             "comments": state.get("comments"),
         }
         return {"audit_log": state.get("audit_log", []) + [entry]}
     ```

     Alternatively, send audit events to an external logging service. Audit trails are essential for compliance.

     **[⬆ Back to Top](#table-of-contents)**

170. ### What are common human-in-the-loop design mistakes?

     Common mistakes include **interrupting too frequently** (causing user fatigue), **failing to capture enough context** for an informed decision, **not persisting state changes properly**, and **allowing untrusted users to resume**. Carefully choose where to interrupt, provide clear instructions, secure the resume pathway, and test end to end. Designing intuitive approval UIs and gracefully handling rejection are also important.

     **[⬆ Back to Top](#table-of-contents)**


## Streaming

171. ### What is streaming in LangGraph?

     Streaming refers to **emitting intermediate events while a graph is running**. Instead of waiting for the entire workflow to finish, you subscribe to a stream of updates — state changes, messages, or custom events. LangGraph's `stream()` method returns an iterator that yields events as soon as they occur, improving UX with real-time feedback.

     ```python
     for event in graph.stream(input_state, stream_mode="updates"):
         print(event)   # yields after each node
     ```

     **[⬆ Back to Top](#table-of-contents)**

172. ### What are streaming modes in LangGraph?

     LangGraph supports several streaming modes:

     | Mode | Yields |
     | --- | --- |
     | `values` | The **entire state** each time it changes |
     | `updates` | Only the **changed keys** since the last event |
     | `messages` | LLM **tokens + message metadata** as they stream |
     | `custom` | **Custom events** emitted via the stream writer |
     | `debug` | Detailed **internal trace** events |

     You can also combine modes: `graph.stream(state, stream_mode=["updates", "messages"])`.

     **[⬆ Back to Top](#table-of-contents)**

173. ### What is the difference between streaming values and updates?

     `values` mode yields the **full state object** on each update, whereas `updates` yields a **dictionary of only the keys that changed** (keyed by node name). In applications with large states (embeddings, document lists), `updates` saves bandwidth and processing. `values` is simpler when you want to display the entire state without merging partial updates.

     **[⬆ Back to Top](#table-of-contents)**

174. ### What is message streaming?

     Message streaming (`stream_mode="messages"`) streams **LLM message tokens as they are generated**, along with metadata. In chat applications, this lets your UI render the assistant's reply token by token as soon as it's produced, rather than waiting for the full response:

     ```python
     for token, metadata in graph.stream(state, stream_mode="messages"):
         print(token.content, end="", flush=True)
     ```

     **[⬆ Back to Top](#table-of-contents)**

175. ### What is custom event streaming?

     Custom event streaming lets you **emit arbitrary events from within a node** using a stream writer. Obtain it with `get_stream_writer()` and call it with your payload. Clients listen for these by subscribing to `stream_mode="custom"`. Useful for progress bars and status updates:

     ```python
     from langgraph.config import get_stream_writer

     def long_task(state: dict) -> dict:
         writer = get_stream_writer()
         for i in range(3):
             writer({"progress": i})   # emit custom event
         return {"done": True}
     ```

     **[⬆ Back to Top](#table-of-contents)**

176. ### What is debug streaming?

     Debug streaming (`stream_mode="debug"`) emits **internal events** such as node execution order, state merges, and routing decisions to help developers understand graph behaviour. It produces a detailed trace. While helpful for debugging, **avoid exposing debug streams in production** because they may include sensitive data.

     **[⬆ Back to Top](#table-of-contents)**

177. ### How do you stream intermediate graph outputs to a UI?

     Call `graph.stream(initial_state, stream_mode="messages")` (or `updates`) and iterate over the events, updating the UI for each. In a web app, use **WebSockets or Server-Sent Events** to push updates to the browser. Handle reconnection and backpressure gracefully:

     ```python
     async def ws_handler(websocket, state, config):
         async for event in graph.astream(state, config, stream_mode="updates"):
             await websocket.send_json(event)
     ```

     **[⬆ Back to Top](#table-of-contents)**

178. ### How do you stream token output from an LLM node?

     If your LLM supports token streaming, use `stream_mode="messages"` and LangGraph will surface tokens automatically as the model generates them. If you cannot stream tokens directly, collect them in a buffer and emit incremental updates via the custom stream writer so the UI can display them as they arrive:

     ```python
     for token, meta in graph.stream(state, stream_mode="messages"):
         if meta["langgraph_node"] == "generate":
             ui.append(token.content)
     ```

     **[⬆ Back to Top](#table-of-contents)**

179. ### How do you show progress for a multi-step graph?

     Use **custom events** to emit progress updates from each node — include current step and total. In the UI, display a progress bar that advances when events arrive. For parallel branches, compute progress as the fraction of completed tasks. Because LangGraph allows dynamic branching (via `Send`), you may need to aggregate progress across subgraphs:

     ```python
     def step_node(state, *, total=5):
         writer = get_stream_writer()
         writer({"type": "progress", "step": state["step"], "total": total})
         return {"step": state["step"] + 1}
     ```

     **[⬆ Back to Top](#table-of-contents)**

180. ### How do you stream tool execution status?

     Wrap tool calls in a node that **emits custom events before and after** execution — a `tool_start` event with the name/args, then the call, then a `tool_end` event with the result or error. Clients listen to show a spinner or display results:

     ```python
     def tool_node(state: dict) -> dict:
         writer = get_stream_writer()
         writer({"type": "tool_start", "name": state["tool_name"]})
         result = run_tool(state["tool_name"], state["tool_args"])
         writer({"type": "tool_end", "result": result})
         return {"tool_result": result}
     ```

     **[⬆ Back to Top](#table-of-contents)**

181. ### How do you handle streaming errors?

     Streaming functions should **catch exceptions and emit error events**. Wrap node logic in try/except; on exception, emit an `error` event with the message (and optionally stack traces for debugging). Ensure the stream **closes gracefully** to prevent hanging clients. For recoverable errors, emit a `retry` event and continue:

     ```python
     def safe_node(state: dict) -> dict:
         writer = get_stream_writer()
         try:
             return {"result": risky(state)}
         except Exception as e:
             writer({"type": "error", "message": str(e)})
             return {"error": str(e)}
     ```

     **[⬆ Back to Top](#table-of-contents)**

182. ### How do you design a responsive chat UI with LangGraph?

     Subscribe to the **`messages` stream** and update the chat window as tokens arrive. Show **typing indicators** when an LLM node runs and **progress bars** for long tasks. Use WebSockets for real-time updates. Map stream events to conversation IDs (`thread_id`) to handle multiple threads. Allow the user to send messages that trigger new graph invocations.

     **[⬆ Back to Top](#table-of-contents)**

183. ### How do you stream partial results from parallel branches?

     When you use `Send` to launch parallel branches, **each branch can emit its own events**. In the merged stream, include a **branch ID** in the payload so the client knows which branch produced each event. As each branch finishes, emit a result event. The UI displays partial results and updates as more branches complete. Reducers merge final results into the state.

     **[⬆ Back to Top](#table-of-contents)**

184. ### How do you avoid exposing internal state in streamed output?

     Be **selective about what you include** in streamed events. Do not emit raw state objects containing sensitive information (API keys, private embeddings). Instead, create **small payloads with only the fields the client needs**. Use data-redaction functions or view models to sanitise output:

     ```python
     def safe_payload(state: dict) -> dict:
         return {"answer": state["answer"]}   # exclude keys, embeddings, PII
     ```

     **[⬆ Back to Top](#table-of-contents)**

185. ### How do you test streaming behaviour?

     Write tests that run the graph in **streaming mode and collect events into a list**, then assert order and content. For async code, use `pytest` and `pytest-asyncio`. Test custom events by mocking the stream writer and asserting it was called with the right arguments:

     ```python
     def test_stream_order():
         events = list(graph.stream({"x": 1}, stream_mode="updates"))
         assert events[0].keys() == {"first_node"}
         assert "result" in events[-1]["last_node"]
     ```

     **[⬆ Back to Top](#table-of-contents)**


## Error Handling & Reliability

186. ### How do you handle node execution failures?

     Encapsulate node logic in **try/except blocks** and return error information in the state. If a node raises, you can retry, route to a fallback node, or propagate the error. For non-critical failures, add an `error` field to record what went wrong. Logging the exception and context is essential for debugging:

     ```python
     def node(state: dict) -> dict:
         try:
             return {"result": do_work(state)}
         except Exception as e:
             logger.exception("node failed")
             return {"error": str(e), "failed": True}
     ```

     **[⬆ Back to Top](#table-of-contents)**

187. ### How do you configure retry policies in LangGraph?

     LangGraph supports a **`RetryPolicy`** that you can attach to a node, automatically retrying on failure with backoff. You can also use the `tenacity` library for finer control:

     ```python
     from langgraph.pregel import RetryPolicy

     builder.add_node("call_api", call_api,
                      retry=RetryPolicy(max_attempts=3,
                                        backoff_factor=2.0))
     ```

     ```python
     # Alternative: tenacity decorator
     from tenacity import retry, stop_after_attempt, wait_exponential

     @retry(stop=stop_after_attempt(3),
            wait=wait_exponential(multiplier=1, min=1, max=4))
     def call_api(state: dict) -> dict:
         return {"result": external_api(state["query"])}
     ```

     **[⬆ Back to Top](#table-of-contents)**

188. ### When should a node be retried?

     Retry nodes when errors are **transient** (network hiccups, rate limits, temporary timeouts) **and** the operation is **idempotent** (safe to repeat). Avoid retries for permanent errors like invalid user input or authentication failures. Respect provider policies and implement backoff to avoid overwhelming APIs.

     **[⬆ Back to Top](#table-of-contents)**

189. ### When should a node not be retried?

     Do **not retry nodes that perform non-idempotent side effects** (sending an email, charging a card) because repeated execution could have unintended consequences. Handle the error gracefully and return an error message instead. Also avoid retries for errors that require **human intervention**, such as invalid credentials or misconfiguration.

     **[⬆ Back to Top](#table-of-contents)**

190. ### How do you handle non-idempotent failures?

     For nodes with side effects, wrap the side-effecting code in an **idempotency guard**. Record a unique identifier before performing the action and check whether it has already been processed before repeating. If a failure occurs **after** the action (e.g., network failure after a payment), implement **compensation logic** (issue a refund, reverse the transaction) or store a ledger entry for manual reconciliation:

     ```python
     def charge(state: dict) -> dict:
         key = state["idempotency_key"]
         if payment_store.exists(key):
             return {"charged": True}          # already done
         payment_store.record(key)
         gateway.charge(state["amount"])
         return {"charged": True}
     ```

     **[⬆ Back to Top](#table-of-contents)**

191. ### How do you implement fallback nodes?

     Add **conditional edges that route to a fallback node** if the primary node fails or returns an error. Set an error flag in the state when something goes wrong; in the routing function, check the flag and decide whether to go to the normal next node or the fallback. The fallback can call a different API, provide a default answer, or ask the user to rephrase:

     ```python
     def route(state: dict) -> str:
         return "fallback" if state.get("error") else "continue"

     builder.add_conditional_edges("primary", route,
         {"continue": "next", "fallback": "fallback_node"})
     ```

     **[⬆ Back to Top](#table-of-contents)**

192. ### How do you handle LLM timeout errors?

     Use the model client's **timeout parameters** to bound execution and catch `TimeoutError`. Implement retries with backoff, and consider **graceful degradation** to a simpler fallback (e.g., summarise available information). Log timeouts to monitor model performance:

     ```python
     llm = ChatOpenAI(model="gpt-4o-mini", timeout=20, max_retries=2)

     def generate(state: dict) -> dict:
         try:
             return {"answer": llm.invoke(state["prompt"]).content}
         except TimeoutError:
             return {"answer": "Sorry, that took too long.", "degraded": True}
     ```

     **[⬆ Back to Top](#table-of-contents)**

193. ### How do you handle tool timeout errors?

     Wrap tool calls in **timeout guards** using `asyncio.wait_for()` for async calls or a watchdog for synchronous ones. Catch timeout exceptions and either retry or return an error. Provide user feedback ("the tool is taking longer than expected") and avoid blocking the workflow indefinitely:

     ```python
     import asyncio

     async def tool_node(state: dict) -> dict:
         try:
             result = await asyncio.wait_for(run_tool(state), timeout=10)
             return {"tool_result": result}
         except asyncio.TimeoutError:
             return {"error": "tool timed out"}
     ```

     **[⬆ Back to Top](#table-of-contents)**

194. ### How do you handle rate limits from model providers?

     Implement a rate-limit handler that detects **HTTP 429** or rate-limit error messages. **Pause and retry** after the recommended wait time using **exponential backoff with jitter** to avoid thundering-herd problems. For high-throughput applications, distribute load across multiple API keys or model endpoints:

     ```python
     from tenacity import retry, retry_if_exception_type, wait_random_exponential

     @retry(retry=retry_if_exception_type(RateLimitError),
            wait=wait_random_exponential(min=1, max=60))
     def call_llm(prompt): return llm.invoke(prompt)
     ```

     **[⬆ Back to Top](#table-of-contents)**

195. ### How do you recover from partial graph failure?

     If a graph fails halfway, **restart execution from the last checkpoint**. Inspect the state to determine where the failure occurred, then either fix the data or route around the failed node. In some cases, skip the failed node and continue with other branches. The ability to resume from checkpoints makes recovery straightforward:

     ```python
     # Resume the same thread after fixing the issue
     graph.invoke(None, config={"configurable": {"thread_id": "t1"}})
     ```

     **[⬆ Back to Top](#table-of-contents)**

196. ### How do checkpoints help with failure recovery?

     Checkpoints capture the **entire state and execution pointer**. On failure, load the last checkpoint and resume from that point — avoiding repeating already-successful work and providing a consistent view of state at the moment of failure. Checkpoints can also implement **rollbacks** by reverting to a previous snapshot using `update_state` with a target checkpoint.

     **[⬆ Back to Top](#table-of-contents)**

197. ### How do you implement circuit breaker behaviour in LangGraph?

     A circuit breaker **prevents a node from being invoked when a downstream service is failing consistently**. Maintain a failure counter and last-failure timestamp in the state or an external store. Before calling the failing service, check whether the threshold is exceeded; if so, skip the call and route to a fallback. After a cooldown, reset the counter:

     ```python
     def call_with_breaker(state, *, store):
         stats = store.get(("breaker",), "api") or {"failures": 0, "open_until": 0}
         if stats["failures"] >= 5 and time.time() < stats["open_until"]:
             return {"error": "circuit_open"}     # skip the call
         try:
             return {"result": external_api(state["q"]), }
         except Exception:
             stats["failures"] += 1
             stats["open_until"] = time.time() + 30
             store.put(("breaker",), "api", stats)
             return {"error": "call_failed"}
     ```

     **[⬆ Back to Top](#table-of-contents)**

198. ### How do you design dead-letter handling for failed tasks?

     Dead-letter handling means **capturing tasks that could not be processed** after retries. Implement a node that appends failed tasks and error details to a **dead-letter queue or persistent store**. Review this queue offline to reprocess, fix, or discard. Dead-letter queues ensure no data is lost when failures occur:

     ```python
     def dead_letter(state: dict) -> dict:
         dlq.append({"task": state["task"], "error": state["error"],
                     "timestamp": now()})
         return {"sent_to_dlq": True}
     ```

     **[⬆ Back to Top](#table-of-contents)**

199. ### How do you log graph failures for debugging?

     Use **structured logging** inside each node to record inputs, outputs, and exceptions. Include the `thread_id`, node name, and correlation IDs for tracing. On failure, log the stack trace along with a state snapshot. Persist logs to a central system (ELK, Datadog). Combining logging with streaming gives **real-time visibility** into the graph's behaviour.

     ```python
     logger.error("node_failed", extra={
         "thread_id": config["configurable"]["thread_id"],
         "node": "generate", "state": redact(state),
     })
     ```

     **[⬆ Back to Top](#table-of-contents)**

200. ### How do you make LangGraph workflows production reliable?

     Production reliability involves **redundancy, monitoring, throttling, and graceful error handling**. Configure **durable checkpointers** so state persists across restarts; implement **retries with backoff**; use **circuit breakers and fallback nodes**; monitor performance and error rates; and test under load. Isolate side-effecting nodes behind queues to decouple them from the main graph. Deploy multiple workers and use load balancers for high concurrency.

     **[⬆ Back to Top](#table-of-contents)**


## Subgraphs & Multi-Agent Systems

201. ### What is a subgraph in LangGraph?

     A **subgraph** is a reusable graph that can be called from within another graph. Subgraphs encapsulate a set of nodes and edges into a single node-like unit. You define a subgraph by creating a `StateGraph`, compiling it, and registering it as a node in a larger graph. Subgraphs promote **modularity and reuse**:

     ```python
     # Subgraph
     sub = StateGraph(SubState)
     sub.add_node("step", step_fn)
     sub.add_edge(START, "step"); sub.add_edge("step", END)
     subgraph = sub.compile()

     # Parent registers the compiled subgraph directly as a node
     parent.add_node("sub", subgraph)
     ```

     **[⬆ Back to Top](#table-of-contents)**

202. ### Why would you split a workflow into subgraphs?

     Splitting into subgraphs improves **maintainability and reusability**. Each subgraph encapsulates a distinct concern (summarisation, sentiment analysis, data extraction) and can be **tested independently**. Subgraphs make the top-level graph easier to read by hiding low-level details. When requirements change, you update a subgraph without affecting the rest of the workflow.

     **[⬆ Back to Top](#table-of-contents)**

203. ### How do subgraphs improve maintainability?

     By **isolating functionality**, subgraphs let developers reason about and test each part separately. If a bug arises, you can narrow it to the responsible subgraph. Subgraphs also encourage **consistent interfaces**: each defines its own state schema and contract, making it clear what inputs are required and what outputs are produced.

     **[⬆ Back to Top](#table-of-contents)**

204. ### How do you pass state between parent graphs and subgraphs?

     When registering a subgraph as a node, you specify how the **parent state maps to the subgraph's input** and how its output maps back. If parent and subgraph **share state keys**, you can add the compiled subgraph directly. If schemas differ, wrap the subgraph in a node that transforms the state:

     ```python
     def call_sub(state: dict) -> dict:
         sub_input = {"task": state["current_task"]}     # map in
         sub_out = subgraph.invoke(sub_input)
         return {"task_result": sub_out["result"]}        # map back
     ```

     **[⬆ Back to Top](#table-of-contents)**

205. ### How do you isolate subgraph state?

     Define a separate **`TypedDict` or Pydantic model** for the subgraph state. When invoking the subgraph, convert the relevant portion of the parent state into the subgraph state. Inside the subgraph, only update its own fields. After completion, map its state back to the parent. This prevents accidental modification of unrelated fields and keeps subgraphs **loosely coupled**.

     **[⬆ Back to Top](#table-of-contents)**

206. ### What is a supervisor agent?

     A **supervisor agent** oversees and coordinates other agents or subgraphs. It assigns tasks to specialised agents, aggregates their outputs, and makes high-level decisions. In LangGraph, a supervisor is a graph whose nodes call other graphs (subagents) and route based on their results. This pattern is useful for **multi-agent systems** where different agents have different skills.

     ```python
     def supervisor(state: dict) -> Command:
         next_agent = llm.invoke(f"Who should handle: {state['task']}?").content
         return Command(goto=next_agent, update={"active_agent": next_agent})
     ```

     **[⬆ Back to Top](#table-of-contents)**

207. ### How do you design a multi-agent system in LangGraph?

     Identify the **roles/skills** required (research, coding, writing) and create a **subgraph per agent**. Design a **supervisor graph** that accepts a task, decides which agent should handle it, and delegates by invoking the appropriate subgraph. Use state fields to track the active agent and aggregate results. Implement turn-taking or parallel execution depending on the use case.

     **[⬆ Back to Top](#table-of-contents)**

208. ### What is the difference between supervisor-based and peer-to-peer multi-agent design?

     In a **supervisor-based** design, a central agent manages the workflow and delegates tasks to specialised subagents — strong coordination but a single point of control. In **peer-to-peer** design, agents communicate directly and decide collaboratively how to proceed. LangGraph can model peer-to-peer via conditional edges and dynamic routing, but coordination without a supervisor requires **careful management of shared state and conflict resolution**.

     | | Supervisor | Peer-to-Peer |
     | --- | --- | --- |
     | Control | Centralised | Distributed |
     | Coordination | Easy | Complex |
     | Single point of failure | Yes (supervisor) | No |
     | Conflict handling | Supervisor mediates | Explicit strategies needed |

     **[⬆ Back to Top](#table-of-contents)**

209. ### How do you route tasks between specialised agents?

     Use a **routing node** that examines the task description or context and determines which agent (subgraph) is best suited, using heuristics, a classifier model, or rules. Once selected, the graph calls the corresponding subgraph and merges its output. For dynamic systems, maintain a **registry of agents and their capabilities** to make routing decisions.

     **[⬆ Back to Top](#table-of-contents)**

210. ### How do you prevent agents from conflicting with each other?

     Conflicts arise when multiple agents modify the **same state fields** or perform incompatible actions. Mitigate by **clearly defining responsibilities** and isolating state. Use **reducers** to merge concurrent updates deterministically. For peer-to-peer systems, implement conflict-resolution strategies (last-writer-wins, version vectors) or have a supervisor mediate.

     **[⬆ Back to Top](#table-of-contents)**

211. ### How do you aggregate outputs from multiple agents?

     After invoking multiple subagents (possibly in parallel via `Send`), **collect their results from the state and combine them**. For example, concatenate lists of suggestions and remove duplicates. Use **reducers** to handle concurrent updates to the same field. Present the aggregated output to the user or feed it into a downstream node:

     ```python
     class State(TypedDict):
         suggestions: Annotated[list, lambda o, n: list(dict.fromkeys(o + n))]
     ```

     **[⬆ Back to Top](#table-of-contents)**

212. ### How do you design a researcher-writer-reviewer workflow?

     Create three subgraphs: **researcher** (retrieves documents), **writer** (generates a draft), and **reviewer** (improves and edits). The supervisor calls the researcher first and stores context, then the writer to create an answer, then the reviewer for quality control. At each stage you can **interrupt for human feedback** or loop until satisfactory:

     ```python
     b.add_edge(START, "researcher")
     b.add_edge("researcher", "writer")
     b.add_edge("writer", "reviewer")
     b.add_conditional_edges("reviewer", lambda s: "writer" if s["needs_revision"] else END,
                             {"writer": "writer", END: END})
     ```

     **[⬆ Back to Top](#table-of-contents)**

213. ### How do you design a planner-executor agent?

     In a **planner-executor** pattern, the planner analyses the request and produces a **plan** (a list of steps/tool calls). The executor iterates through the plan, performing each step. Represent the plan in the state (e.g., a queue). A loop node pops the next step and routes to the appropriate tool or subgraph, continuing until the plan is complete:

     ```python
     def executor(state: dict) -> dict:
         plan = state["plan"]
         if not plan:
             return {"is_done": True}
         step, rest = plan[0], plan[1:]
         result = run_step(step)
         return {"plan": rest, "results": [result]}
     ```

     **[⬆ Back to Top](#table-of-contents)**

214. ### How do you design a code-review multi-agent system?

     Model separate agents for **static analysis, unit tests, and human review**. The supervisor first invokes static analysis to catch obvious issues. If the code passes, run the unit-test agent in a **sandboxed environment**. Finally, send results to a human review agent or real reviewer. Automate approvals for low-risk changes and require human intervention for high-impact code.

     **[⬆ Back to Top](#table-of-contents)**

215. ### How do you debug multi-agent graph behaviour?

     Trace **how tasks are delegated and how agents interact**. Use streaming (with subgraph events enabled via `subgraphs=True`) to monitor events from all agents, including custom events emitted when tasks are assigned or completed. Inspect the state after each agent finishes to confirm expected fields are updated. **Logging and visualising** the supervisor's execution order helps identify mis-routed tasks or deadlocks:

     ```python
     for event in graph.stream(state, stream_mode="updates", subgraphs=True):
         print(event)   # includes (namespace, update) for subgraph nodes
     ```

     **[⬆ Back to Top](#table-of-contents)**


## RAG with LangGraph

216. ### How do you build a RAG pipeline using LangGraph?

     A **Retrieval-Augmented Generation (RAG)** pipeline retrieves relevant documents and uses them to generate answers. In LangGraph, create nodes for: (1) query rewriting; (2) document retrieval; (3) optional reranking; (4) answer generation; and (5) final formatting. Connect them with edges:

     ```python
     from langgraph.graph import StateGraph, START, END
     from typing import TypedDict

     class RAGState(TypedDict):
         question: str
         query: str
         docs: list
         answer: str

     b = StateGraph(RAGState)
     b.add_node("rewrite", rewrite_query)
     b.add_node("retrieve", retrieve_docs)
     b.add_node("rerank", rerank)
     b.add_node("generate", generate_answer)
     b.add_edge(START, "rewrite")
     b.add_edge("rewrite", "retrieve")
     b.add_edge("retrieve", "rerank")
     b.add_edge("rerank", "generate")
     b.add_edge("generate", END)
     rag = b.compile()
     ```

     **[⬆ Back to Top](#table-of-contents)**

217. ### Why use LangGraph for RAG instead of a simple retrieval chain?

     A simple retrieval chain retrieves documents and feeds them to an LLM in one step. LangGraph lets you add **intermediate steps** — query rewriting, multi-source retrieval, reranking, and hallucination checks. You can **branch on retrieval quality**, loop if no good context is found, and persist conversation state for follow-ups. The graph structure also makes it easy to integrate **human verification** or fall back to a tool call when the model is unsure.

     **[⬆ Back to Top](#table-of-contents)**

218. ### How do you add query rewriting to a LangGraph RAG workflow?

     Include a node that calls an LLM to **rewrite the user's query** into a more effective search query. Pass the original question and produce a rewritten query in the state. Downstream retrieval uses the rewritten query. You can also add logic to decide when rewriting is necessary (based on query length or ambiguity):

     ```python
     def rewrite_query(state: dict) -> dict:
         prompt = f"Rewrite this into a concise search query: {state['question']}"
         return {"query": llm.invoke(prompt).content.strip()}
     ```

     **[⬆ Back to Top](#table-of-contents)**

219. ### How do you add document retrieval as a node?

     Create a node that interfaces with your retrieval system (vector store or search API). It takes the query from the state and returns a list of documents:

     ```python
     def retrieve_docs(state: dict) -> dict:
         query = state["query"]
         docs = vector_store.similarity_search(query, k=5)
         return {"docs": docs}
     ```

     Chain this after the query-rewrite node and persist retrieved documents so later nodes (reranking, generation) can use them.

     **[⬆ Back to Top](#table-of-contents)**

220. ### How do you add reranking as a node?

     Create a node that **scores retrieved documents by relevance** (using a cross-encoder model or heuristics), sorts them, and returns the top results:

     ```python
     def rerank(state: dict) -> dict:
         docs = state["docs"]
         scored = sorted(docs, key=lambda d: relevance_score(state["query"], d),
                         reverse=True)
         return {"docs": scored[:3]}
     ```

     Reranking improves the quality of context fed to the answer generator and reduces noise.

     **[⬆ Back to Top](#table-of-contents)**

221. ### How do you add answer generation as a node?

     After retrieving and reranking, **call an LLM with a prompt that includes the question and selected context**. Return the model's answer and optionally the sources:

     ```python
     def generate_answer(state: dict) -> dict:
         context = "\n\n".join(d.page_content for d in state["docs"])
         prompt = (f"Answer the question using only the context.\n\n"
                   f"Context:\n{context}\n\nQuestion: {state['question']}")
         return {"answer": llm.invoke(prompt).content}
     ```

     You can also stream the answer tokens using `stream_mode="messages"`.

     **[⬆ Back to Top](#table-of-contents)**

222. ### How do you add hallucination checking to a RAG graph?

     Add a node **after answer generation** that checks whether the answer is supported by the retrieved documents — using a classifier/grader LLM or heuristics verifying that facts appear in the docs. If the answer fails, route back to retrieval to fetch more context or ask the user to rephrase:

     ```python
     def check_grounding(state: dict) -> dict:
         verdict = grader_llm.invoke(
             f"Is this answer grounded in the context? yes/no\n"
             f"Answer: {state['answer']}\nContext: {state['docs']}").content
         return {"grounded": verdict.strip().lower() == "yes"}

     def route(state: dict) -> str:
         return "done" if state["grounded"] else "retrieve"
     ```

     **[⬆ Back to Top](#table-of-contents)**

223. ### How do you add source validation to a RAG graph?

     In source validation, **ensure documents come from trustworthy sources**. Add a node that filters documents based on metadata (domain, publication date, author) and returns only valid ones. If none remain, fall back to a different retrieval method or ask the user for more information. Display sources alongside the answer for transparency:

     ```python
     TRUSTED = {"docs.internal", "wikipedia.org"}

     def validate_sources(state: dict) -> dict:
         valid = [d for d in state["docs"] if d.metadata["source"] in TRUSTED]
         return {"docs": valid, "no_valid_source": not valid}
     ```

     **[⬆ Back to Top](#table-of-contents)**

224. ### How do you handle no-context-found scenarios?

     If retrieval returns **no useful documents**, branch to a node that either uses a different retrieval strategy (broaden the query), informs the user that no context was found, or asks for more details. **Avoid hallucinating** an answer when there is no supporting evidence:

     ```python
     def route_retrieval(state: dict) -> str:
         return "generate" if state["docs"] else "broaden_search"
     ```

     **[⬆ Back to Top](#table-of-contents)**

225. ### How do you route between vector search and web search?

     Implement a **routing node** that analyses the question and chooses the retrieval method — web search for recent events, vector store for a known corpus. You can also run **both in parallel via `Send`** and merge results. Conditional edges make this routing easy to express:

     ```python
     def choose_retriever(state: dict) -> str:
         if any(w in state["question"].lower() for w in ["today", "latest", "news"]):
             return "web_search"
         return "vector_search"

     b.add_conditional_edges("router", choose_retriever,
         {"web_search": "web_search", "vector_search": "vector_search"})
     ```

     **[⬆ Back to Top](#table-of-contents)**

226. ### How do you implement corrective RAG using LangGraph?

     **Corrective RAG (CRAG)** iteratively refines the answer: grade retrieved documents, and if they are insufficient, **rewrite the query and re-retrieve** (or fall back to web search) before generating. Loop between answer generation and retrieval until the answer is accurate or a max iteration count is reached:

     ```python
     def grade_docs(state: dict) -> dict:
         relevant = [d for d in state["docs"] if is_relevant(state["question"], d)]
         return {"docs": relevant, "needs_web": len(relevant) == 0}

     def route(state: dict) -> str:
         return "web_search" if state["needs_web"] else "generate"
     ```

     **[⬆ Back to Top](#table-of-contents)**

227. ### How do you implement adaptive RAG using LangGraph?

     **Adaptive RAG** adjusts its retrieval strategy based on the question type or user preferences. Use conditional routing to select between methods (high-precision vs. high-recall) or adjust the number of documents returned. Include nodes that **update the retrieval configuration** in the state (e.g., `k=10` for complex questions). Adaptive RAG can also tune summarisation length or answer style based on feedback:

     ```python
     def classify_complexity(state: dict) -> dict:
         level = llm.invoke(f"simple/complex? {state['question']}").content
         return {"k": 10 if "complex" in level else 3}
     ```

     **[⬆ Back to Top](#table-of-contents)**

228. ### How do you implement agentic RAG using LangGraph?

     **Agentic RAG** treats retrieval and generation as **actions within an agent loop**. Instead of a linear pipeline, the agent decides whether to search, summarise, ask for clarification, or answer. Build an agent graph where the LLM node outputs commands like `search`, `read`, `answer`, or `stop`. The routing function maps these to retrieval, reading, or generation nodes. Loop until the agent decides to stop, combining RAG with agentic reasoning.

     **[⬆ Back to Top](#table-of-contents)**

229. ### How do you cache retrieval results in LangGraph?

     Caching reduces latency and cost. Store recent queries and their document lists in a **store keyed by the query string or a hash**. In the retrieval node, check the cache first; if a result exists, return it instead of querying again. Include a **TTL** to prevent stale data:

     ```python
     import hashlib

     def retrieve_cached(state, *, store):
         key = hashlib.sha256(state["query"].encode()).hexdigest()
         cached = store.get(("retrieval_cache",), key)
         if cached:
             return {"docs": cached.value}
         docs = vector_store.similarity_search(state["query"], k=5)
         store.put(("retrieval_cache",), key, [d.page_content for d in docs])
         return {"docs": docs}
     ```

     **[⬆ Back to Top](#table-of-contents)**

230. ### How do you evaluate a LangGraph-based RAG system?

     Measure **answer accuracy, relevance of retrieved documents, latency, and user satisfaction**. Use benchmarks (open-domain QA datasets) to compare answers against ground truth. Analyse **retrieval recall and precision**. Measure end-to-end latency and identify bottlenecks (retrieval vs. generation). Collect user feedback and adjust the graph. Tools like LangSmith and `ragas` help automate evaluation of faithfulness and answer relevancy.

     **[⬆ Back to Top](#table-of-contents)**


## Testing

231. ### How do you unit test LangGraph nodes?

     Unit testing nodes means **isolating the node function and passing a controlled state**. Use `pytest` or `unittest`. Mock dependencies (LLM calls, API requests) so tests stay deterministic. Assert that nodes return the expected state updates and handle edge cases:

     ```python
     def test_prepare_draft():
         state = {}
         result = prepare_draft(state)
         assert "draft" in result
         assert result["approved"] is False
     ```

     **[⬆ Back to Top](#table-of-contents)**

232. ### How do you integration test a full graph?

     Integration tests run the **compiled graph end to end** with realistic state and dependencies. Use a test checkpointer and store to capture state across invocations. Simulate user input and assert the final state matches expectations:

     ```python
     def test_rag_returns_answer():
         graph = build_rag_graph().compile(checkpointer=MemorySaver())
         out = graph.invoke({"question": "What is LangGraph?"},
                            {"configurable": {"thread_id": "t1"}})
         assert out["answer"]
         assert out["docs"]
     ```

     You can also run the graph in streaming mode and verify the sequence of events.

     **[⬆ Back to Top](#table-of-contents)**

233. ### How do you mock LLM responses in LangGraph tests?

     Mocking ensures tests do **not rely on external APIs**. Create a fake LLM with the same interface returning a predetermined answer, and inject it via dependency injection. LangChain also provides `FakeListChatModel` / `FakeMessagesListChatModel` for this:

     ```python
     from langchain_core.language_models.fake_chat_models import FakeListChatModel

     def test_generate_with_mock():
         fake = FakeListChatModel(responses=["mock answer"])
         out = generate_answer({"question": "hi", "docs": []}, llm=fake)
         assert out["answer"] == "mock answer"
     ```

     Alternatively, use `unittest.mock.patch` to patch the LLM call.

     **[⬆ Back to Top](#table-of-contents)**

234. ### How do you test conditional routing?

     Test routing by **providing states that exercise each branch**. Create test cases with different field values and assert the routing function returns the expected key. Instrument the graph (or use debug streaming) to record the node sequence. Coverage testing ensures all branches are handled:

     ```python
     import pytest

     @pytest.mark.parametrize("action,expected", [
         ("search", "search"), ("answer", "answer"), ("xyz", "fallback"),
     ])
     def test_route(action, expected):
         assert route({"next_action": action}) == expected
     ```

     **[⬆ Back to Top](#table-of-contents)**

235. ### How do you test graph state updates?

     Invoke nodes with an initial state and **verify the returned updates merge correctly**. Test reducers by simulating concurrent updates and asserting the merge logic behaves as intended (appending to a list, taking a max). For complex graphs, run a small scenario and inspect the final state:

     ```python
     def test_messages_reducer():
         from operator import add
         assert add(["a"], ["b"]) == ["a", "b"]

     def test_node_merge():
         out = graph.invoke({"count": 0})
         assert out["count"] == 1
     ```

     **[⬆ Back to Top](#table-of-contents)**

236. ### How do you test human-in-the-loop flows?

     Simulate an interrupt by invoking the graph and capturing the interrupt. Then **simulate the human response** by invoking again with the same `thread_id` and a `Command(resume=...)`. Verify the graph resumes from the correct point and produces the expected outcome. In tests, bypass real UIs by injecting messages directly:

     ```python
     def test_approval_flow():
         graph = build_approval_graph().compile(checkpointer=MemorySaver())
         cfg = {"configurable": {"thread_id": "t1"}}
         graph.invoke({}, cfg)                       # runs until interrupt
         out = graph.invoke(Command(resume="approve"), cfg)
         assert out["result"] == "sent"
     ```

     **[⬆ Back to Top](#table-of-contents)**


## Observability & Monitoring

237. ### How do you trace LangGraph execution?

     Enable **debug streaming** to capture detailed events — node start/end, state updates, routing decisions — to understand execution order and diagnose issues. Integrate with **LangSmith** or your own tracing system to visualise the graph and inspect intermediate state. Setting the `LANGCHAIN_TRACING_V2` environment variable auto-traces runs:

     ```python
     import os
     os.environ["LANGCHAIN_TRACING_V2"] = "true"
     os.environ["LANGCHAIN_API_KEY"] = "ls-..."
     # Now every graph.invoke() is traced in LangSmith
     ```

     **[⬆ Back to Top](#table-of-contents)**

238. ### How do you use LangSmith with LangGraph?

     LangSmith **records and analyses LLM interactions**. With tracing enabled, LangGraph automatically logs each node's prompts, responses, tool calls, latencies, and token usage as a nested trace. You can inspect the call hierarchy and intermediate state, identify prompt issues, run evaluations, and monitor model performance over time. No code changes are needed beyond setting the environment variables.

     **[⬆ Back to Top](#table-of-contents)**

239. ### What metrics should you monitor for LangGraph agents?

     | Metric | Why it matters |
     | --- | --- |
     | **Latency per node** | Identify slow steps |
     | **Success / failure rates** | Reliability |
     | **Retry counts** | Transient instability |
     | **Token consumption** | Cost control |
     | **Interrupts / approvals** | HITL workflow health |
     | **Recursion depth** | Detect runaway loops |
     | **Retrieval recall / answer quality** | RAG effectiveness |

     Use dashboards to visualise these over time and alert when thresholds are exceeded.

     **[⬆ Back to Top](#table-of-contents)**

240. ### How do you monitor latency per node?

     Wrap each node in a **timing decorator** that records start/end timestamps and logs the duration. Store metrics in a monitoring system and break latency down by node type (LLM call, retrieval, tool). Use **percentiles** (P50, P95) to understand typical and worst-case performance, then optimise slow nodes:

     ```python
     import time, functools

     def timed(name):
         def deco(fn):
             @functools.wraps(fn)
             def wrap(state, *a, **k):
                 t0 = time.perf_counter()
                 out = fn(state, *a, **k)
                 metrics.observe(f"node.{name}.latency", time.perf_counter() - t0)
                 return out
             return wrap
         return deco
     ```

     **[⬆ Back to Top](#table-of-contents)**

241. ### How do you monitor token usage in LangGraph workflows?

     Most LLM providers return **token counts in the response metadata** (`response.usage_metadata`). Extract these in your node and accumulate them in the state or a monitoring system. Track prompt tokens, completion tokens, and total cost. Implement **budgets or alerts** when usage exceeds thresholds. Token tracking helps manage cost and detect runaway loops:

     ```python
     def generate(state: dict) -> dict:
         resp = llm.invoke(state["prompt"])
         usage = resp.usage_metadata
         return {"answer": resp.content,
                 "tokens": state.get("tokens", 0) + usage["total_tokens"]}
     ```

     **[⬆ Back to Top](#table-of-contents)**

242. ### How do you monitor tool failure rates?

     Record **success and error counts for each tool**. Capture tool name, error type, and context via logging/metrics. Calculate failure rate as `errors / (successes + errors)` and monitor trends. High failure rates may indicate API issues, input-validation problems, or network instability. Implement **alerts** to investigate and mitigate:

     ```python
     def tool_node(state: dict) -> dict:
         try:
             result = run_tool(state)
             metrics.increment(f"tool.{state['tool_name']}.success")
             return {"tool_result": result}
         except Exception as e:
             metrics.increment(f"tool.{state['tool_name']}.error")
             return {"error": str(e)}
     ```

     **[⬆ Back to Top](#table-of-contents)**


## Deployment & Production

243. ### How do you deploy a LangGraph application?

     Package your graph, dependencies, and model credentials into a **container or virtual environment**. Expose an **API endpoint** (FastAPI or Flask) that accepts user requests, invokes the graph, and streams responses. Deploy to AWS ECS, Kubernetes, or serverless functions. Configure a **durable checkpointer** (Redis, Postgres) and store. Use environment variables or secret managers for credentials:

     ```python
     from fastapi import FastAPI
     from fastapi.responses import StreamingResponse

     app = FastAPI()
     graph = build_graph().compile(checkpointer=checkpointer, store=store)

     @app.post("/chat")
     async def chat(req: ChatRequest):
         config = {"configurable": {"thread_id": req.thread_id}}
         async def gen():
             async for ev in graph.astream({"messages": [("user", req.text)]},
                                           config, stream_mode="messages"):
                 yield ev[0].content
         return StreamingResponse(gen(), media_type="text/event-stream")
     ```

     You can also deploy via the **LangGraph Platform / LangGraph Server**, which provides a managed runtime with built-in persistence, streaming, and an assistants API.

     **[⬆ Back to Top](#table-of-contents)**

244. ### How do you scale LangGraph workers?

     Scale **horizontally** by running multiple workers that process graph invocations in parallel. Use a **load balancer or task queue** to distribute requests. Ensure your checkpointer and store handle **concurrent access** (Redis or a scalable database). For streaming workloads, use **asynchronous I/O** (`astream`) to handle many connections efficiently. Because state lives in the shared checkpointer, any worker can resume any thread.

     **[⬆ Back to Top](#table-of-contents)**

245. ### How do you manage graph versions in production?

     Maintain **version numbers** for your graph code and state schemas. Tag Docker images or releases accordingly. When deploying a new version, run **migration scripts** to convert existing checkpoints, or start new threads for the new version. Keep old versions running until existing conversations complete. Use **feature flags** to gradually roll out new graphs.

     **[⬆ Back to Top](#table-of-contents)**

246. ### How do you roll back a LangGraph deployment?

     If a deployment introduces bugs, **revert to the previous version** of the graph and dependencies. Because checkpoints capture state, ensure the new version did not make **incompatible schema changes**. Roll back by switching traffic to the previous container image or code branch. Keep multiple versions available and route threads based on their version ID to avoid breaking in-flight conversations.

     **[⬆ Back to Top](#table-of-contents)**

247. ### How do you secure API keys used inside graph nodes?

     **Never hardcode API keys**. Store them in environment variables or secret-management services (AWS Secrets Manager, HashiCorp Vault). Inject keys at runtime. **Restrict key scope** and rotate regularly. In logs and streams, **redact or hash** keys to avoid leaks:

     ```python
     import os
     llm = ChatOpenAI(api_key=os.environ["OPENAI_API_KEY"])  # from secret manager
     ```

     **[⬆ Back to Top](#table-of-contents)**

248. ### How do you protect user data in LangGraph state?

     Follow security best practices: **encrypt sensitive data** at rest and in transit, apply **least privilege** to stores and checkpointers, and **do not expose the full state** to clients. Use field-level encryption for particularly sensitive fields. Provide mechanisms for users to **view and delete** their data. Comply with data-protection regulations (GDPR, CCPA) and document data flows for audits.

     **[⬆ Back to Top](#table-of-contents)**

249. ### How do you design LangGraph for high concurrency?

     Ensure the **checkpointer, store, and model APIs scale horizontally**. Use **asynchronous nodes** where possible to avoid blocking threads. Partition work across workers and **minimise shared state** to reduce contention. Use `Send` to fan out tasks and aggregate results. Monitor resource usage (CPU, memory, connections) and **autoscale based on load**. Apply rate limiting and connection pooling for downstream services.

     **[⬆ Back to Top](#table-of-contents)**

250. ### How would you design a production-grade AI assistant using LangGraph end to end?

     Designing a production-grade assistant involves multiple components:

     - **State schema** — define a robust state model capturing user messages, tool results, context, and metadata.
     - **Nodes** — create nodes for planning, tool execution, error handling, streaming, and memory updates. Use **subgraphs** for modular tasks (retrieval, summarisation, code execution).
     - **Control flow** — connect nodes with conditional edges for branching, loops, and parallelism. Use `Send` for concurrent tasks and `Command` for dynamic routing.
     - **Persistence** — configure durable checkpointers and stores to persist conversation state and user preferences.
     - **Human-in-the-loop** — add interrupt points before high-impact actions, with a UI for approvals.
     - **Streaming** — stream messages and custom events to update the UI in real time.
     - **Reliability** — implement retries, fallbacks, circuit breakers, and monitoring. Isolate functionality with subgraphs for independent testing.
     - **Security** — encrypt sensitive data, manage secrets, and enforce access controls.
     - **Observability** — trace via LangSmith, monitor latency/tokens/failures, and alert on anomalies.

     ```python
     # High-level composition
     assistant = (
         StateGraph(AssistantState)
         .add_node("plan", planner)
         .add_node("tools", tool_node)
         .add_node("retrieve", retrieval_subgraph)
         .add_node("approve", approval_node)
         .add_node("respond", responder)
     )
     # ... wire edges, then:
     graph = assistant.compile(checkpointer=PostgresSaver(...), store=store)
     ```

     Combine these pieces into a cohesive graph, deploy on scalable infrastructure, monitor performance, and iterate based on user feedback. By leveraging LangGraph's stateful orchestration, you build an assistant that is **flexible, reliable, and easy to extend**.

     **[⬆ Back to Top](#table-of-contents)**

---

### Disclaimer

The questions and answers in this repository are a curated summary of commonly asked LangGraph interview questions. They cover concepts from foundational through production-grade depth, including state management, nodes and edges, commands, persistence, streaming, error handling, subgraphs, RAG integration, testing, observability, and deployment. There is no guarantee that these exact questions will appear in any given interview — the purpose is to help you rapidly review key concepts and build deep understanding. APIs evolve, so always verify syntax against the official LangGraph documentation for your installed version. Contributions and corrections are welcome.

Good luck with your interview 😊

---
