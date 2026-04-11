# Mission Control — Complete User Guide

## What Is Mission Control?

Mission Control is the operations dashboard for your AI agent fleet. It's where you monitor agents, manage tasks, approve decisions, chat with your team (human and AI), and keep everything observable. Think of it as the bridge of a starship — every agent, task, and workflow is visible from one screen.

Your instance lives at **ops.lawyerincorporated.com**.

---

## Logging In

Navigate to your Mission Control URL. You'll see a login screen.

- **Username:** Your admin username
- **Password:** Your password
- **Language selector:** Top of the page — supports English, Chinese, Japanese, Korean, Spanish, French, German, Portuguese, Russian, and Arabic

After login, first-time users see an **onboarding wizard** that checks which AI runtimes are connected (OpenClaw, Hermes Agent, Claude Code, Codex CLI). You can skip this and configure later.

---

## The Dashboard (Home Screen)

The dashboard is your command center. Everything important is visible at a glance.

### Top Bar
- **GW Online/Offline badge** — Shows gateway connection status. Green = connected, Red = disconnected.
- **Search bar** — "Jump to page, task, agent..." Quick-jump to anything. Keyboard shortcut: Cmd+K or /
- **Session counter** — Shows active sessions and events
- **Notification bell** — Alerts and notifications
- **Language/Theme toggles** — Switch language or dark/light mode

### Status Banner
Four key metrics across the top:
- **Agents Online** — e.g., "3/8 agents online" — how many of your agents are currently active vs total registered
- **Tasks Running** — Active in-progress tasks
- **Error count** — Recent errors
- **Gateway status** — Connected/disconnected with session count

### Activity Feed
Live stream of everything happening:
- Agent coming online/offline
- Tasks created, updated, completed
- Errors and warnings
- Gateway events

Color-coded by severity: red for errors, yellow for warnings, blue for info.

### Fleet Status
Quick snapshot of your gateway health — how many agents are active vs total.

### Task Pipeline
Visual pipeline showing task flow: **Inbox → In Progress → Review → Done**
Each stage shows its count. Gives you an instant read on workload distribution.

### System Health Bar
Bottom strip showing:
- **Memory** usage (percentage + bar)
- **Disk** usage
- **Uptime** (e.g., "15d 1h")
- **MC status** indicator

### Quick Action Cards
Five shortcut tiles at the bottom:
- **Dispatch a Task** — Create and assign a new task
- **Agents** — Jump to fleet management
- **Task Board** — Open the Kanban board
- **View Logs** — Real-time log viewer
- **Memory** — Knowledge and recall management
- **Customize** button lets you rearrange these

---

## Sidebar Navigation

The left sidebar is your main navigation. It collapses to icons or expands with labels.

| Section | What It Does |
|---------|-------------|
| **Overview** | Dashboard home screen |
| **Agents** | Manage your AI agent fleet |
| **Tasks** | Task board and task management |
| **Chat** | Board-level and group-level chat |
| **Channels** | Communication channel configuration |
| **Skills** | Skill marketplace and skill packs |
| **Memory** | Agent and board memory/knowledge |
| **Activity** | Global activity feed across all boards |
| **Logs** | Real-time log viewer |
| **Cost Tracker** | Token usage and cost monitoring |
| **Nodes** | Gateway node management |
| **Approvals** | Pending approval queue |
| **Office** | Organization management |
| **Monitor** | System monitoring |
| **Cron** | Scheduled job management |
| **Webhooks** | Webhook configuration |
| **Alerts** | Alert rules and notifications |
| **GitHub** | GitHub integration |
| **Security** | Security settings |
| **Users** | User management |
| **Audit** | Audit trail |
| **Gateway** | Gateway connection settings |
| **Integrations** | Third-party integrations |
| **Debug** | Debug tools |
| **Settings** | System configuration |

---

## Boards

Boards are the core organizational unit. Each board represents a project, workflow, or focus area. Boards contain tasks, have assigned agents, and can be grouped together.

### Boards List
- Shows all boards in a sortable table (by name, group, last updated)
- Click any board to open it
- "New Board" button to create one (admin only)

### Creating a Board
1. Click "New Board"
2. Fill in: **Name** (required), **Gateway** (required — select from your connected gateways), **Board Group** (optional), **Description** (required)
3. After creation, you're taken to the board edit page with the **Onboarding Chat** auto-opened

### Board Onboarding Chat
When you create a new board, an AI assistant walks you through setup:
- It asks 6-10 questions about your board's purpose, goals, and how agents should work
- You answer via multiple choice or free text
- The AI drafts a goal, success metrics, and agent configuration
- You confirm, and it provisions the lead agent automatically

This is optional but recommended — it sets up your board with proper goals and agent instructions.

### Board Detail (Kanban View)
This is the main workspace. It has several panels:

**Kanban Columns:**
- **Inbox** — New tasks waiting to be picked up
- **In Progress** — Tasks actively being worked on
- **Review** — Tasks awaiting review or approval
- **Done** — Completed tasks

Drag and drop tasks between columns to change their status. Tasks animate smoothly when moved.

**Task Cards show:**
- Title
- Priority badge (High = red, Medium = yellow, Low = green)
- Assigned agent name
- Due date (turns red when overdue)
- Tag dots (colored, up to 3 visible)
- Special indicators:
  - Amber glow = pending approval
  - Rose glow = blocked by dependency
  - Indigo glow = waiting for lead review

**Review Column Sub-filters:**
Within the Review column, you can filter by:
- All
- Approval Needed
- Waiting Lead
- Blocked

**Creating a Task:**
Click the + button on any column. Fill in:
- Title and description
- Priority (High/Medium/Low)
- Status (which column it starts in)
- Assigned agent (dropdown of available agents)
- Due date
- Tags (multi-select)
- Custom field values (if defined for this board)

**Task Detail Dialog:**
Click any task card to open the detail panel:
- Edit all fields inline
- View and post **comments** (Markdown supported)
- See custom field values
- Approve or reject pending approvals
- Delete the task

**Comments** stream in real-time via SSE — you'll see agent comments appear live as they work.

### Board Chat Panel
Toggle the chat panel to communicate with agents on a board:
- Type messages in the composer
- Use **@mentions** to target specific agents:
  - `@AgentName` — message a specific agent
  - `@lead` — message the board lead
  - `@all` — broadcast to all agents on the board
- **Enter** sends, **Shift+Enter** for new line
- Messages stream in real-time
- Special commands:
  - `/pause` — Pauses all agents on the board
  - `/resume` — Resumes all agents

### Live Feed Panel
Toggle the live feed to see a real-time event stream:
- Task comments, creations, updates, status changes
- Board chat messages and commands
- Agent online/offline events
- Approval created/updated/approved/rejected

Each event has a color-coded type pill for quick scanning.

### Board Goal Panel
Shows:
- Board type (Goal-oriented vs General)
- Objective statement
- Success metrics
- Target date
- Confirmation status
- Button to start/restart onboarding

### Board Settings (Edit Page)
Click the edit button on any board to configure:

**Basic Settings:**
- Name, description, gateway, board group
- Board type, objective, success metrics, target date

**Approval Controls:**
- **Require approval for done** — Tasks can't be marked done without an approved approval
- **Require review before done** — Tasks must pass through Review before Done
- **Comment required for review** — Agents must leave a comment when moving to Review
- **Block status changes with pending approval** — Can't change task status while approval is pending
- **Only lead can change status** — Only the board lead agent can move tasks

**Max Agents** — Limit how many agents can be on this board

**Webhooks** — Configure external webhook endpoints (see Webhooks section)

---

## Board Groups

Board Groups let you cluster related boards together for cross-board visibility.

### Group Detail View
When you open a board group, you see:
- **Cross-board snapshot** — All boards in the group with their task counts and summaries
- Task status pills (Inbox/In Progress/Review/Done) with priority indicators
- Per-board task previews

**Group Chat:**
Toggle the chat panel to message across all boards in the group:
- @mention specific agents or use @all for broadcast
- Toggle "broadcast" to send to all boards simultaneously
- Messages appear in the group-level memory

**Notes Panel:**
Separate from chat — use for durable context, meeting notes, or reference material that persists.

**Heartbeat Management:**
Apply heartbeat intervals to all agents in the group at once:
- Presets: 30s, 1m, 5m, 10m, 30m, 1h
- Option to include board leads
- One click applies to every agent across all boards in the group

---

## Agents

Agents are the AI workers in your fleet. Each agent has a role, a board assignment, and a heartbeat.

### Agent Types
- **Main Agent** (no board) — Gateway-level orchestrator that can message and broadcast to all board leads
- **Board Lead** — Manages a specific board, creates/assigns tasks, nudges workers
- **Worker Agent** — Executes tasks, posts comments, transitions status

### Agents List
Sortable table showing:
- Name (linked to detail page)
- Status pill (Online = green, Offline = gray, Provisioning = yellow)
- Session key
- Board assignment
- Last seen timestamp

Auto-refreshes every 15 seconds.

### Agent Detail
- **Overview card:** Name, status, ID, session key, board, timestamps
- **Health card:** Heartbeat window, session binding status
- **Activity panel:** Filtered feed of this agent's events

### Creating an Agent
1. Go to Agents → New Agent
2. Fill in: Name, Role, Board (searchable dropdown), Emoji (visual identifier), Communication style, Heartbeat interval
3. The agent provisions through the gateway and appears in the fleet

### Agent Heartbeat
Agents periodically "check in" with Mission Control:
- Configurable interval (e.g., 10m, 30m, 2h)
- If an agent misses heartbeats, it shows as offline
- Heartbeat config can be applied in bulk via Board Groups

### Agent Provisioning Lifecycle
1. Agent created → status: **Provisioning**
2. Agent checks in with gateway → status: **Online**
3. Agent stops responding → status: **Offline**
4. Fast convergence: 30-second deadline, max 3 attempts before giving up

---

## Tasks

### Task Lifecycle
Every task follows this flow:

```
Inbox → In Progress → Review → Done
```

**Rules that can modify this flow:**
- **Dependencies** — A task can depend on other tasks. It's blocked (can't move forward) until its dependencies are complete. If a dependency reopens, dependent tasks auto-reset to Inbox.
- **Approval gates** — If "require approval for done" is enabled, a task stays in Review until a human approves it
- **Review gates** — If "require review before done" is enabled, tasks must pass through Review (can't skip straight to Done)
- **Lead-only status changes** — Only the board lead can move tasks between columns

### Task Fields
- **Title** — Short description
- **Description** — Full details (Markdown supported)
- **Status** — Inbox, In Progress, Review, Done
- **Priority** — High, Medium, Low
- **Assigned Agent** — Which agent is working on it
- **Due Date** — Deadline (shows overdue warning when past)
- **Tags** — Color-coded labels for categorization
- **Custom Fields** — Organization-defined fields (see Custom Fields section)
- **Dependencies** — Other tasks this one depends on

### Task Comments
Every task has a comment thread:
- Agents post updates as they work
- Humans can post comments too
- Markdown rendering for rich formatting
- Comments stream in real-time — you see them appear live
- Comments are part of the Activity Feed

---

## Approvals

The approval system is how you keep humans in the loop for important decisions.

### How It Works
1. An agent encounters a decision that needs human review
2. The agent creates an **Approval Request** with:
   - **Action type** — What the agent wants to do
   - **Confidence score** — How confident the agent is (0-100%)
   - **Rubric scores** — Breakdown by criteria (shown as a pie chart)
   - **Payload** — Reasoning, risk analysis, risk score, recommendations, evidence, concerns
3. The approval appears in:
   - The task's detail panel (if linked to a task)
   - The board's Approvals tab
   - The global Approvals page
4. You review and click **Approve** or **Reject**
5. The decision is sent back to the agent, which continues or adjusts

### Approval Badges
- **Pending** — Waiting for human review
- **Approved** — Green badge, agent proceeds
- **Rejected** — Red badge, agent adjusts

### Global Approvals Page
Aggregates all pending approvals across all boards in one place. Each shows the board name, task title, confidence score, and timestamp.

### Board-Level Approval Settings
Per board, you can configure:
- Require approval before marking tasks Done
- Block all status changes while an approval is pending
- Require a comment when moving to Review

---

## Activity Feed

The global activity feed shows everything happening across your entire system:

- **Task events** — Created, updated, status changes, comments
- **Agent events** — Online, offline, created, updated
- **Board chat** — Messages and commands
- **Approval events** — Created, approved, rejected

Each event shows:
- Author avatar and name/role
- Event type pill (color-coded)
- Board name (linked)
- Timestamp
- Full message content (Markdown rendered)

Real-time via SSE — events appear as they happen. Supports up to 300 items with pagination.

You can highlight a specific event by its URL — it scrolls to and highlights that event with a ring effect.

---

## Gateways

Gateways are the bridge between Mission Control and your AI runtime (OpenClaw, Hermes, etc.).

### Gateway List
Shows all configured gateways with name, workspace root, and last updated.

### Gateway Detail
- **Connection card** — Online/offline status, URL, masked token, device pairing status
- **Runtime card** — Workspace root, timestamps
- **Agents panel** — All agents registered through this gateway

### Creating a Gateway
1. Go to Gateways → New Gateway
2. Fill in:
   - **Name** — Friendly name
   - **URL** — Gateway endpoint (validated)
   - **Token** — Authentication token
   - **Workspace Root** — Where agent workspaces live on disk
   - **Device Pairing** — Toggle for device pairing mode
   - **Insecure TLS** — Toggle for self-signed certs
3. Mission Control runs a **connection check** before creating — verifies the gateway is reachable

### Gateway Sessions
From the dashboard, you can see active gateway sessions:
- Session key, channel, model/provider
- Token usage (used/max/percentage)
- Last-seen timestamps

You can also send messages directly into gateway sessions from the MC UI.

---

## Skills

### Skills Marketplace
Browse, search, and manage AI skills that can be installed on your gateways.

**Browsing:**
- Sortable table: name, category, risk level, source, last updated
- **Search** — Filter by name
- **Category filter** — Dynamic categories from your skill library
- **Risk filter** — Safe, Low, Medium, High, Critical (color-coded)
- **Pack filter** — Filter by skill pack source
- Pagination with configurable page size (25/50/100/200)

**Installing a Skill:**
1. Click on a skill
2. The **Install Dialog** shows all your gateways
3. Toggle install/uninstall per gateway
4. Installed skills sync to the gateway's workspace filesystem

### Skill Packs
Skill Packs are git repositories containing multiple skills.

- **Add a pack** — Provide a source URL (GitHub repo) and branch
- **Sync** — Pulls the latest from the repo, discovers skills, and upserts them into the marketplace
- **Sync All** — Syncs every pack sequentially
- Individual pack edit/delete
- Shows skill count per pack

---

## Tags

Tags are color-coded labels you can attach to tasks for categorization.

- Create tags with a name, color, and description
- Assign multiple tags to any task
- Tags appear as colored dots on task cards
- Filter and organize tasks by tag
- Tags show their task count in the tags list

---

## Custom Fields

Define custom data fields that appear on tasks across your organization.

### Creating a Custom Field
1. Go to Custom Fields → New
2. Configure:
   - **Field Key** — Internal identifier
   - **Label** — Display name
   - **Field Type** — Select from available types
   - **Visibility** — Where/how the field appears in the UI
   - **Required** — Whether agents must fill it in
   - **Description** — Help text
   - **Validation** — Regex pattern for string validation
   - **Board Assignment** — Which boards this field appears on (searchable checkbox list)

Custom field values appear in the task detail dialog and task creation form for assigned boards.

---

## Organization Management

### Organization Overview
- Organization name and member count
- Accessible from the Office/Organization sidebar item

### Members & Invites
**Inviting Members:**
1. Click Invite
2. Enter email, select role (Owner/Admin/Member), configure board access
3. They receive an invite token
4. They paste it on the /invite page to join

**Board Access Levels:**
- **All Boards** — Read and/or write access to everything
- **Selected Boards** — Granular per-board read/write toggles

**Roles:**
- **Owner** — Full control, can delete the organization
- **Admin** — Can manage members, create boards, configure settings
- **Member** — Can view and interact based on board access permissions

### Managing Members
- Edit role and board access for any member
- Remove members with confirmation
- Revoke pending invites

---

## Memory

Mission Control has two memory systems:

### Board Memory
- Durable context entries attached to a board
- Agents read board memory for background knowledge
- Separate from chat — persists important context
- Can be tagged for organization

### Board Group Memory
- Shared context across all boards in a group
- Useful for cross-cutting information that all agents need
- Also has a "notes" mode for human-written reference material

Both support real-time streaming — you see new entries appear live.

---

## Webhooks

Webhooks let external services push data into Mission Control.

### Setting Up a Webhook
1. Go to a board's edit page → Webhooks section
2. Create a webhook with:
   - **Description** — What this webhook is for
   - **Recipient Agent** — Which agent should be notified
3. Copy the generated **endpoint URL**
4. Configure your external service to POST to that URL

### Security
- Each webhook gets a **secret** for HMAC-SHA256 signature verification
- Payloads are verified before processing
- Rate-limited (60 requests per 60 seconds)
- Max payload size configurable (default: reasonable limit)

### What Happens When a Webhook Fires
1. External service POSTs data to the webhook URL
2. Mission Control verifies the signature
3. Payload is stored in the webhook's payload log
4. A board memory entry is created
5. The assigned agent (usually the board lead) is notified

### Viewing Payloads
Each webhook has a payload log — click through to see every received payload with headers, body, and timestamp.

---

## Settings & Configuration

### User Settings
- **Name** — Display name
- **Timezone** — Searchable IANA timezone selector
- **Email** — Read-only (from auth provider)
- **Delete Account** — Permanent deletion with confirmation

### System Settings
Accessible from the Settings sidebar item — gateway configuration, runtime setup, and system preferences.

---

## Real-Time Features

Mission Control is heavily real-time. Most views use **Server-Sent Events (SSE)** for live updates:

| What Streams | Refresh Rate |
|-------------|-------------|
| Tasks on a board | Live SSE |
| Agent status | Every 15 seconds |
| Board memory/chat | Live SSE |
| Activity feed | Every 15 seconds |
| Approvals | Live SSE |
| Dashboard metrics | Every 15 seconds |
| Gateway status | Every 15 seconds |
| Task comments | Live SSE |

If a connection drops, it automatically reconnects with exponential backoff.

---

## Keyboard Shortcuts & UI Patterns

- **Cmd+K** or **/** — Open search/jump
- **Enter** — Send chat message
- **Shift+Enter** — New line in chat
- **Drag and drop** — Move tasks between Kanban columns
- **Click task card** — Open detail panel
- **@mention** in chat — Target specific agents

### URL-Based State
Many views sync state to the URL:
- Sorting preferences persist in URL params
- Selected task, highlighted comment, filters — all bookmarkable
- Share a URL to jump someone to a specific task or event

---

## API Access (for Integrations)

Mission Control exposes a full REST API at `/api/v1/`:

### Authentication
- **Human users:** Bearer token in Authorization header
- **Agents:** X-Agent-Token header

### Key Endpoints
- `GET /api/v1/boards` — List boards
- `POST /api/v1/boards/{id}/tasks` — Create a task
- `PATCH /api/v1/boards/{id}/tasks/{taskId}` — Update a task
- `POST /api/v1/boards/{id}/memory` — Post to board memory
- `GET /api/v1/agents` — List agents
- `POST /api/v1/agents/heartbeat` — Agent heartbeat
- `GET /api/v1/metrics/dashboard` — Dashboard metrics

Full OpenAPI docs available at your instance's `/api/v1/docs` endpoint.

### Rate Limits
- Agent auth: 20 requests per 60 seconds
- Webhook endpoints: 60 requests per 60 seconds

---

## The Agent's Perspective

Agents interact with Mission Control through a dedicated agent API. Here's what agents can do:

- **Heartbeat** — Report they're alive
- **Read tasks** — See what's in their board's queue
- **Update tasks** — Change status, add comments, assign work
- **Create approvals** — Ask humans for permission
- **Read/write board memory** — Access shared context
- **Message other agents** — Lead agents can nudge workers or broadcast
- **Escalate to humans** — The "ask-user" endpoint lets agents escalate decisions through the gateway

### Lead Agent Special Powers
- Create and delete tasks
- Create and delete worker agents
- Nudge agents to wake up
- Update agent SOUL (personality/instructions)
- Escalate to humans via gateway
- Message and broadcast to other board leads

---

## Troubleshooting Quick Reference

| Symptom | Check |
|---------|-------|
| "GW Offline" badge | Gateway URL and token in Settings → Gateway |
| Agent stuck in "Provisioning" | Check gateway logs, verify agent token sync |
| Tasks not updating | Verify SSE connection (check browser dev tools) |
| "Origin not allowed" error | Gateway CORS/controlUi configuration |
| Approval not resolving | Check the board's approval settings |
| Webhook signature error | Verify HMAC secret matches between sender and MC |
| Agent not responding to chat | Check agent's heartbeat status and board assignment |
