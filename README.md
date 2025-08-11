# Kylo AI - Feature-Driven Development Agent

**Kylo AI** is a sophisticated feature-driven development agent designed to guide developers through a complete software development lifecycle using structured documentation workflows. It bridges the gap between high-level feature requests and complete implementation through six specialized modes.

## Core Philosophy

The **KYLO** name represents the operational philosophy:

- **K**nowledge gathering and requirements analysis
- **Y**ielding technical designs and architecture
- **L**everaging systematic task breakdown
- **O**perating through comprehensive review and implementation

## Overview

Kylo AI operates through distinct modes that create and maintain structured feature documentation. Each feature gets a unique number and standardized documentation in `docs/features/###-feature-name/` with requirements, design, task artifacts, and memory preservation for cross-session continuity.

### Key Features

- **Artifact-Driven Development**: Each mode produces specific, standardized documentation
- **Memory-Enhanced Operations**: Critical decisions and patterns preserved across sessions
- **Quality Gates**: Dependencies prevent skipping critical planning steps
- **Minimal Overhead**: Focus on essential documentation without over-engineering
- **Test-Driven Implementation**: BUILD mode emphasizes TDD and validation
- **Skeptical Review**: Built-in critical analysis before implementation
- **Progress Tracking**: Real-time status updates throughout development
- **Pattern Recognition**: Apply successful approaches from previous features

## Operating Modes

### 1. REQUIREMENT Mode

**File**: `kylo-ai-requirement.prompt.md`  
**Purpose**: Transform feature requests into clear functional requirements  
**Focus**: WHAT and WHY, never HOW  
**Artifact Created**: `###-requirements.md`  
**Dependencies**: None (starting point)

**Key Responsibilities**:

- Analyze current product state and feature fit
- Document clear, testable requirements
- Define scope boundaries (included/excluded)
- Establish business value justification
- Create problem statements and acceptance criteria

### 2. DESIGN Mode

**File**: `kylo-ai-design.prompt.md`  
**Purpose**: Convert requirements into comprehensive technical architecture  
**Focus**: HOW to implement with multiple approaches  
**Artifact Created**: `###-design.md`  
**Dependencies**: Requires existing requirements document

**Key Responsibilities**:

- Deep codebase analysis for informed decisions
- Present multiple implementation approaches
- Design data models and API interfaces
- Plan component architecture and interactions
- Include comprehensive testing strategy
- Seek developer validation on technical preferences

### 3. TASK Mode

**File**: `kylo-ai-task.prompt.md`  
**Purpose**: Break technical designs into actionable implementation tasks  
**Focus**: Minimal, executable task breakdown  
**Artifact Created**: `###-tasks.md`  
**Dependencies**: Requires existing design document

**Key Responsibilities**:

- Convert design into fewest possible tasks
- Create short, action-oriented task names
- Organize tasks in logical implementation phases
- Map dependencies between tasks
- Reference design document rather than duplicate details

### 4. REVIEW Mode

**File**: `kylo-ai-review.prompt.md`  
**Purpose**: Skeptical validation of all artifacts before implementation  
**Focus**: Implementation readiness assessment  
**Artifact**: Updates existing artifacts or provides recommendations  
**Dependencies**: Requires at least design document

**Key Responsibilities**:

- Perform critical analysis of requirements and design
- Assess implementation viability and risks
- Make clear go/no-go recommendations
- Identify gaps and suggest remediation
- Validate that design addresses all requirements

### 5. BUILD Mode

**File**: `kylo-ai-build.prompt.md`  
**Purpose**: Systematic implementation following documented plans  
**Focus**: Test-driven development with progress tracking  
**Artifact**: Updates tasks document with progress  
**Dependencies**: Requires all three artifacts (requirements, design, tasks)

**Key Responsibilities**:

- Execute tasks sequentially with validation
- Follow test-driven development approach
- Update task completion status in real-time
- Validate functionality before proceeding
- Document blockers and seek clarification when needed

### 6. REFACTOR Mode

**File**: `kylo-ai-refactor.prompt.md`  
**Purpose**: Systematically modify existing features with full change tracking  
**Focus**: Update all artifacts while preserving history  
**Artifact**: Updates all existing artifacts with version tracking  
**Dependencies**: Requires at least requirements document

**Key Responsibilities**:

- Hydrate all existing feature artifacts
- Analyze change impact and scope
- Update requirements with version tracking
- Evolve design to accommodate changes
- Add new tasks while preserving completed ones
- Maintain full change traceability
- Document migration strategies
- Preserve backward compatibility considerations

## Documentation Structure

All features follow a standardized folder structure:

```
docs/features/
├── 001-feature-name/
│   ├── 001-requirements.md    # Business requirements (REQUIREMENT mode)
│   ├── 001-design.md         # Technical design (DESIGN mode)
│   ├── 001-tasks.md          # Implementation tasks (TASK mode)
│   ├── 001-memory.md         # Feature memory and context
│   └── 001-decisions.md      # Critical decision log
├── 002-another-feature/
│   ├── 002-requirements.md
│   ├── 002-design.md
│   ├── 002-tasks.md
│   ├── 002-memory.md
│   └── 002-decisions.md
```

### Artifact Standards

**Requirements Document (`###-requirements.md`)**:

- Clear, concise functional requirements
- Focus on WHAT and WHY, not HOW
- No technical implementation details
- Business justification and user impact

**Design Document (`###-design.md`)**:

- Technical architecture and implementation approach
- Code snippets, data flows, UML diagrams as needed
- Sufficient detail for complete implementation
- Test plan and philosophy
- Multiple implementation proposals when appropriate

**Tasks Document (`###-tasks.md`)**:

- Checklist of implementation tasks
- Short, concise task names
- References back to design document
- Minimal details, maximum actionability
- Organized in logical phases

**Memory Document (`###-memory.md`)**:

- Session history and cross-session continuity
- Critical decisions with full context preservation
- Cross-feature relationships and dependencies
- Patterns applied and lessons learned
- Implementation experience and insights

**Decisions Document (`###-decisions.md`)**:

- Chronological log of all critical decisions
- Complete rationale and alternatives considered
- Impact assessment and review schedules
- Context preservation for future reference

## Workflow Dependencies

The modes have clear dependencies creating a logical development flow:

```
REQUIREMENT (No deps) → DESIGN → TASK → REVIEW → BUILD
                          ↑         ↑       ↑
                          └─────────┴───────┘
                        (REVIEW can analyze any artifacts)

         REFACTOR → Updates all artifacts systematically
            ↓
         REVIEW (validates refactored plans)
```

1. **REQUIREMENT** → No dependencies (starting point)
2. **DESIGN** → Requires requirements
3. **TASK** → Requires design
4. **REVIEW** → Requires at least design (can review any artifacts)
5. **BUILD** → Requires all three artifacts
6. **REFACTOR** → Requires at least requirements (updates all existing artifacts)

## Usage Examples

### Starting a New Feature

```
User: "I need a user authentication system"
→ Kylo AI activates REQUIREMENT mode
→ Creates 001-user-authentication/001-requirements.md
```

### Continuing Development

```
User: "Design the authentication system from feature 001"
→ Kylo AI activates DESIGN mode
→ Analyzes 001-requirements.md
→ Creates 001-design.md with technical architecture
```

### Implementation

```
User: "Build feature 001"
→ Kylo AI validates all artifacts exist
→ Activates BUILD mode
→ Executes tasks systematically with progress tracking
```

### Refactoring Existing Features

```
User: "Refactor feature 001 to add multi-tenant support"
→ Kylo AI activates REFACTOR mode
→ Loads all 001 artifacts
→ Updates requirements, design, and tasks with changes
→ Preserves completed work and history
```

### Reviewing Refactored Features

```
User: "Review the refactored plan for feature 001"
→ Kylo AI activates REVIEW mode
→ Validates change coherence
→ Assesses migration complexity
→ Provides go/no-go for refactored implementation
```

## Quality Standards

### Requirements Quality

- Requirements are clear and testable
- No technical implementation details included
- Business justification is evident
- Scope is clearly defined
- Document stands alone without additional context

### Design Quality

- Design addresses all functional requirements
- Technical approach is sound and implementable
- Integration with existing codebase is well-planned
- Testing strategy is comprehensive
- Multiple options presented when appropriate

### Implementation Quality

- Follows test-driven development principles
- All functionality works as specified
- Code meets quality and style standards
- Progress accurately tracked and documented
- Proper validation at each step

## Strategic Value

Kylo AI addresses common software development challenges:

- **Requirements Drift**: Clear functional requirements prevent scope creep
- **Design Gaps**: Comprehensive technical planning before coding
- **Implementation Chaos**: Structured task breakdown with dependencies
- **Quality Issues**: Built-in review and validation processes
- **Progress Opacity**: Real-time tracking and status updates
- **Knowledge Transfer**: Standardized documentation for team collaboration
- **Context Loss**: Memory preservation across sessions and team members
- **Decision Amnesia**: Critical decision tracking with full rationale
- **Pattern Reinvention**: Reuse of successful approaches from previous features

## Getting Started

1. **Choose a Mode**: Select the appropriate prompt file based on your current need
2. **Follow Dependencies**: Ensure prerequisite artifacts exist
3. **Create Documentation**: Use the structured templates provided
4. **Iterate as Needed**: Move between modes as requirements evolve
5. **Maintain Quality**: Use REVIEW mode to validate before implementation

## File Structure

```
kylo-ai/
├── README.md                          # This documentation
├── kylo-ai.chatmode.md               # Main chatmode configuration
├── kylo-ai-requirement.prompt.md    # REQUIREMENT mode
├── kylo-ai-design.prompt.md         # DESIGN mode
├── kylo-ai-task.prompt.md           # TASK mode
├── kylo-ai-review.prompt.md         # REVIEW mode (enhanced for refactoring)
├── kylo-ai-build.prompt.md          # BUILD mode
├── kylo-ai-refactor.prompt.md       # REFACTOR mode (new)
├── kylo-ai-complete.prompt.md       # Complete lifecycle mode
├── kylo-ai-analyze.prompt.md        # Alternative requirement mode
└── templates/                        # Memory and decision templates
    ├── memory-template.md
    └── decisions-template.md
```

## Best Practices

1. **Start with Requirements**: Always begin with clear functional requirements
2. **Validate Dependencies**: Ensure prerequisite artifacts exist before proceeding
3. **Use Review Mode**: Critically analyze designs before implementation
4. **Track Progress**: Maintain real-time task completion status
5. **Document Decisions**: Capture reasoning behind technical choices
6. **Test Continuously**: Follow TDD principles during BUILD mode
7. **Maintain Artifacts**: Keep documentation current as features evolve
8. **Preserve Memory**: Update memory files to capture insights and patterns
9. **Apply Lessons**: Use successful patterns from previous features
10. **Review Decisions**: Periodically reassess critical decisions for continued relevance
11. **Refactor Systematically**: Use REFACTOR mode for feature changes to maintain history
12. **Preserve Context**: Never lose the rationale behind original decisions
13. **Track Versions**: Maintain clear version history in refactored artifacts
14. **Validate Changes**: Always review refactored plans before implementation

---

**Kylo AI ensures that features are thoroughly planned, technically sound, and systematically implemented with full documentation and memory preservation throughout the development lifecycle.**
