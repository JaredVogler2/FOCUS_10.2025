# FOCUS Production Scheduling Dashboard

<div align="center">

![FOCUS Dashboard](https://img.shields.io/badge/FOCUS-Production%20Scheduler-blue?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.8+-green?style=for-the-badge&logo=python)
![Flask](https://img.shields.io/badge/Flask-3.0.0-black?style=for-the-badge&logo=flask)
![OR-Tools](https://img.shields.io/badge/OR--Tools-9.14-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

**Advanced Production Scheduling and Optimization Platform**

[Features](#features) • [Quick Start](#quick-start) • [Documentation](#documentation) • [API](#api-reference) • [Contributing](#contributing)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Architecture](#architecture)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Usage Guide](#usage-guide)
- [Dashboard Views](#dashboard-views)
- [Optimization Engine](#optimization-engine)
- [API Reference](#api-reference)
- [Configuration](#configuration)
- [Project Structure](#project-structure)
- [Data Format](#data-format)
- [Scenarios](#scenarios)
- [Development](#development)
- [Testing](#testing)
- [Deployment](#deployment)
- [Troubleshooting](#troubleshooting)
- [Performance](#performance)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## 🎯 Overview

FOCUS (Factory Optimization and Capacity Utilization System) is an advanced production scheduling dashboard that leverages Google OR-Tools' CP-SAT constraint programming solver to optimize manufacturing schedules. The system provides real-time visibility into production planning, resource allocation, and capacity management through an intuitive web interface.

### What It Does

FOCUS transforms complex production scheduling challenges into optimized, actionable plans by:

- **Analyzing** task dependencies, resource constraints, and delivery requirements
- **Optimizing** schedules using advanced constraint programming algorithms
- **Visualizing** production timelines, resource utilization, and bottlenecks
- **Comparing** multiple scheduling scenarios to find the best approach
- **Exporting** schedules for integration with ERP and MES systems

### Use Cases

- **Manufacturing Planning**: Schedule production tasks across multiple teams and shifts
- **Resource Optimization**: Maximize utilization while respecting capacity constraints
- **Delivery Planning**: Ensure on-time delivery while minimizing makespan
- **What-If Analysis**: Compare different scheduling strategies and resource allocations
- **Capacity Planning**: Identify bottlenecks and optimize workforce allocation

---

## 🚀 Key Features

### Optimization Engine

- ✅ **CP-SAT Constraint Solver**: Leverages Google OR-Tools for optimal scheduling
- ✅ **Multi-Constraint Handling**: Task dependencies, resource capacity, quality gates
- ✅ **Priority-Based Scheduling**: Global priority lists with flexible optimization
- ✅ **Late Delivery Management**: Configurable penalties and delay parameters
- ✅ **Team Capacity Planning**: Dynamic workforce allocation across shifts

### Dashboard Capabilities

- 📊 **Multiple View Modes**: Management, IE, Supply Chain, Worker, Team Lead perspectives
- 📈 **Real-Time Metrics**: Makespan, on-time delivery rate, resource utilization
- 🔄 **Scenario Comparison**: Side-by-side analysis of baseline vs optimized schedules
- 📅 **Interactive Gantt Charts**: Drag-and-drop capable timeline visualization
- 📁 **Data Export**: CSV/Excel export for downstream systems

### Analysis Features

- 🔍 **Task-Level Visibility**: Detailed breakdown of each task assignment
- 👥 **Worker Assignment Tracking**: Individual mechanic schedules and workload
- 📦 **Product-Centric Views**: Track all tasks associated with each product
- ⚡ **Bottleneck Identification**: Highlight resource constraints and conflicts
- 📊 **Utilization Analysis**: Team-level and shift-level capacity metrics

### Scenario Modeling

1. **Baseline**: Current scheduling approach with existing constraints
2. **Scenario 1**: CSV-driven headcount optimization
3. **Scenario 3**: Full CP-SAT optimization with minimal workforce

---

## 🏗️ Architecture

### Technology Stack

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend Layer                        │
│  HTML5 • CSS3 • Vanilla JavaScript • Chart.js           │
└─────────────────────────────────────────────────────────┘
                           ↕
┌─────────────────────────────────────────────────────────┐
│                  Application Layer                       │
│  Flask 3.0 • Flask-CORS • Blueprints (Modular Routes)  │
└─────────────────────────────────────────────────────────┘
                           ↕
┌─────────────────────────────────────────────────────────┐
│                   Business Logic                         │
│  Scheduler Engine • Scenario Manager • Data Exporter    │
└─────────────────────────────────────────────────────────┘
                           ↕
┌─────────────────────────────────────────────────────────┐
│                  Optimization Engine                     │
│  Google OR-Tools CP-SAT • Constraint Solver             │
└─────────────────────────────────────────────────────────┘
                           ↕
┌─────────────────────────────────────────────────────────┐
│                      Data Layer                          │
│  Pandas DataFrames • CSV Data Loader                    │
└─────────────────────────────────────────────────────────┘
```

### System Components

**Frontend Components**
- `dashboard-js.js`: Main dashboard controller and UI logic
- `dashboard.css`: Responsive styling and layout
- `templates/`: Jinja2 templates for server-side rendering
- `partials/`: Modular view components for different perspectives

**Backend Components**
- `app.py`: Flask application factory and configuration
- `blueprints/`: Modular route handlers for different features
- `scheduler/`: Core scheduling engine and algorithms
- `exporter.py`: Data export functionality

**Core Scheduler Modules**
- `main.py`: ProductionScheduler class and main API
- `algorithms.py`: Scheduling algorithms and heuristics
- `cp_sat_solver.py`: OR-Tools constraint programming integration
- `constraints.py`: Constraint definitions and validation
- `data_loader.py`: CSV parsing and data transformation
- `metrics.py`: Performance metrics and KPI calculations
- `scenarios.py`: Scenario management and comparison
- `validation.py`: Schedule validation and conflict detection

---

## 📋 Prerequisites

### System Requirements

- **Operating System**: Windows 10+, macOS 10.14+, Linux (Ubuntu 20.04+)
- **Python**: 3.8 or higher (3.9+ recommended)
- **Memory**: 4GB RAM minimum (8GB+ recommended for large datasets)
- **Disk Space**: 100MB for application + data

### Required Software

- Python 3.8+ with pip
- Web browser (Chrome, Firefox, Safari, Edge - latest versions)
- Git (for version control)
- Virtual environment tool (venv, conda, or virtualenv)

### Optional Tools

- Docker (for containerized deployment)
- PostgreSQL (for production data persistence)
- Redis (for caching and session management)
- Nginx (for production web server)

---

## 💻 Installation

### Method 1: Standard Installation

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/FOCUS-dashboard.git
cd FOCUS-dashboard

# 2. Create virtual environment
python -m venv venv

# 3. Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# 4. Install dependencies
pip install -r requirements.txt

# 5. Verify installation
python -c "import ortools; print('OR-Tools installed successfully')"
```

### Method 2: Using Conda

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/FOCUS-dashboard.git
cd FOCUS-dashboard

# 2. Create conda environment
conda create -n focus python=3.9
conda activate focus

# 3. Install dependencies
pip install -r requirements.txt
```

### Method 3: Docker Installation

```bash
# Build Docker image
docker build -t focus-dashboard .

# Run container
docker run -p 5000:5000 focus-dashboard
```

### Dependencies

The `requirements.txt` includes:

```txt
flask==3.0.0          # Web framework
flask-cors==4.0.0     # CORS support for API
pandas==2.1.4         # Data manipulation
numpy==1.26.2         # Numerical computing
ortools==9.14.6206    # Constraint programming solver
```

---

## 🎬 Quick Start

### 1. Start the Application

```bash
# Activate your virtual environment (if not already active)
source venv/bin/activate  # macOS/Linux
# or
venv\Scripts\activate     # Windows

# Run the application
python run.py
```

You should see output like:
```
================================================================================
Initializing Production Scheduler Dashboard
================================================================================

Scheduler loaded successfully!
Total task instances: 145

----------------------------------------
Running ALL scenarios...
✓ Baseline complete: 42.5 days makespan
✓ Scenario 1 complete: 38.2 days makespan
✓ Scenario 3 complete: 35.8 days makespan

================================================================================
All scenarios completed successfully!
================================================================================

 * Running on http://0.0.0.0:5000
```

### 2. Access the Dashboard

Open your web browser and navigate to:
```
http://localhost:5000
```

You'll see the landing page with the FOCUS logo and animation.

### 3. Explore the Dashboard

Click **"Launch Dashboard"** to access the main interface.

### 4. Try Different Views

Use the navigation tabs to explore:
- **Management View**: High-level overview and KPIs
- **IE View**: Industrial engineering analysis
- **Supply Chain**: Material and delivery tracking
- **Worker Gantt**: Individual mechanic schedules
- **Team Lead**: Team-based task assignments
- **Scenarios**: Compare optimization results

---

## 📖 Usage Guide

### Basic Workflow

1. **Load Data**: Place your CSV file in the root directory (default: `scheduling_data.csv`)
2. **Start Server**: Run `python run.py`
3. **View Results**: Navigate to http://localhost:5000/dashboard
4. **Analyze Scenarios**: Compare baseline vs optimized schedules
5. **Export Data**: Download results as CSV for further analysis

### Understanding the Interface

#### Landing Page
- Entry point with branding and quick access
- "Launch Dashboard" button navigates to main interface

#### Dashboard Header
- **View Tabs**: Switch between different perspectives
- **Scenario Selector**: Choose which scenario to display
- **Export Button**: Download current view as CSV
- **Refresh Button**: Reload data from server

#### Main Content Area
- **Metrics Panel**: Key performance indicators
- **Data Table**: Task/product listings with sorting
- **Gantt Chart**: Visual timeline (in applicable views)
- **Filters**: Refine displayed data

### Interpreting Results

#### Key Metrics

**Makespan**: Total time to complete all tasks (in days)
- Lower is better
- Indicates overall schedule efficiency

**On-Time Delivery Rate**: Percentage of products delivered by due date
- Higher is better (target: 95%+)
- Critical for customer satisfaction

**Resource Utilization**: Percentage of team capacity used
- Balanced utilization (70-85%) is ideal
- Too low: wasted capacity
- Too high: bottlenecks and delays

**Max Lateness**: Worst-case delivery delay
- Lower is better
- Indicates scheduling cushion

#### Color Coding

- 🟢 **Green**: On time, within capacity
- 🟡 **Yellow**: At capacity, moderate delay
- 🔴 **Red**: Over capacity, significant delay

---

## 📊 Dashboard Views

### Management View

**Purpose**: Executive-level overview of production schedule and KPIs

**Features**:
- Scenario comparison table
- Key metrics dashboard
- Product-level summary
- Delivery status tracking

**Best For**:
- Daily standup reviews
- Executive reporting
- High-level decision making

**Key Insights**:
- Which scenario performs best
- Overall delivery performance
- Major schedule differences

---

### Industrial Engineering View

**Purpose**: Detailed analysis of scheduling efficiency and optimization

**Features**:
- Task-level breakdown
- Team utilization charts
- Bottleneck identification
- Capacity analysis

**Best For**:
- Process improvement
- Capacity planning
- Efficiency optimization

**Key Insights**:
- Resource constraints
- Task duration analysis
- Optimization opportunities

---

### Supply Chain View

**Purpose**: Material flow and delivery timeline tracking

**Features**:
- Product delivery dates
- Late part impact analysis
- Dependency tracking
- Critical path visualization

**Best For**:
- Delivery coordination
- Material planning
- Risk assessment

**Key Insights**:
- Late delivery risks
- Material bottlenecks
- Critical dependencies

---

### Worker Gantt View

**Purpose**: Individual mechanic schedules and workload

**Features**:
- Per-worker timeline
- Task assignments
- Workload distribution
- Skill-based filtering

**Best For**:
- Daily task assignment
- Workload balancing
- Individual planning

**Key Insights**:
- Who's overloaded
- Schedule conflicts
- Available capacity

---

### Team Lead View

**Purpose**: Team-level coordination and management

**Features**:
- Team-based grouping
- Shift scheduling
- Quality gate tracking
- Team performance metrics

**Best For**:
- Team coordination
- Shift planning
- Performance monitoring

**Key Insights**:
- Team utilization
- Shift distribution
- Quality milestones

---

### Scenario View

**Purpose**: Compare different scheduling approaches

**Features**:
- Side-by-side comparison
- Metric deltas
- What-if modeling
- Prioritization simulation

**Best For**:
- Strategy evaluation
- Resource allocation decisions
- Optimization validation

**Key Insights**:
- Impact of optimization
- Resource requirement changes
- Trade-off analysis

---

## ⚙️ Optimization Engine

### Scheduling Algorithms

#### 1. Global Priority List (Baseline)

**Method**: Heuristic scheduling with task prioritization

**How It Works**:
1. Calculate task priorities based on due dates, dependencies, and criticality
2. Sort tasks by priority (highest first)
3. Assign tasks to earliest available time slot
4. Respect resource capacity and dependencies
5. Handle quality gates and late parts

**Advantages**:
- Fast execution (< 1 second)
- Predictable behavior
- Easy to understand

**Limitations**:
- May not find optimal solution
- Sensitive to priority weights
- Limited constraint handling

**Configuration**:
```python
scheduler.generate_global_priority_list(
    allow_late_delivery=True,
    silent_mode=False
)
```

---

#### 2. CP-SAT Constraint Programming (Scenario 3)

**Method**: Mathematical optimization using constraint satisfaction

**How It Works**:
1. Define decision variables (task start times, worker assignments)
2. Add constraints (dependencies, capacity, quality gates)
3. Set objective function (minimize makespan)
4. Solve using branch-and-bound with cutting planes
5. Return optimal or near-optimal solution

**Advantages**:
- Finds optimal or near-optimal solutions
- Handles complex constraints elegantly
- Proven mathematical guarantees

**Limitations**:
- Slower for large problems (10-60 seconds)
- May timeout on very large datasets
- Requires careful constraint modeling

**Configuration**:
```python
result = scheduler.scenario_3_optimal_schedule(
    max_solve_time_seconds=60,
    num_workers=None  # Auto-calculate minimum workforce
)
```

---

### Constraint Types

#### Hard Constraints (Must Be Satisfied)

1. **Task Dependencies**: Predecessor tasks must complete first
2. **Resource Capacity**: Cannot exceed team/worker capacity
3. **Quality Gates**: Build must complete before quality tasks
4. **Shift Availability**: Tasks only scheduled during work hours
5. **Skill Requirements**: Workers must have required skills

#### Soft Constraints (Optimized)

1. **Due Date Preferences**: Prefer on-time delivery
2. **Resource Utilization**: Balance workload across teams
3. **Task Continuity**: Minimize context switching
4. **Worker Preferences**: Respect skill specialization

---

### Optimization Objectives

The scheduler optimizes for:

1. **Primary**: Minimize total makespan (completion time)
2. **Secondary**: Maximize on-time delivery rate
3. **Tertiary**: Minimize resource count (labor cost)
4. **Quaternary**: Balance workload distribution

**Objective Function**:
```
Minimize: α·makespan + β·late_penalty + γ·workforce_cost + δ·workload_variance
```

Where:
- α = 1.0 (makespan weight)
- β = 10.0 (late delivery penalty)
- γ = 0.1 (labor cost weight)
- δ = 0.05 (balance weight)

---

## 🔌 API Reference

### Scenario Endpoints

#### Get Scenario Data
```http
GET /api/scenarios/<scenario_id>
```

**Response**:
```json
{
  "scenarioId": "baseline",
  "makespan": 42.5,
  "onTimeRate": 87.3,
  "maxLateness": 5.2,
  "totalWorkforce": 12,
  "tasks": [...],
  "products": [...],
  "teamCapacities": {...},
  "utilization": {...}
}
```

---

#### Run What-If Scenario
```http
POST /api/scenarios/run-what-if
Content-Type: application/json

{
  "productId": "Product_A",
  "priorityBoost": 10
}
```

**Response**:
```json
{
  "success": true,
  "originalMakespan": 42.5,
  "newMakespan": 39.8,
  "improvement": 2.7,
  "affectedTasks": [...]
}
```

---

#### Compare Scenarios
```http
GET /api/scenarios/compare?scenario1=baseline&scenario2=scenario3
```

**Response**:
```json
{
  "scenario1": {...},
  "scenario2": {...},
  "deltas": {
    "makespan": -6.7,
    "onTimeRate": +8.5,
    "workforce": -3
  }
}
```

---

### Assignment Endpoints

#### Get Worker Assignments
```http
GET /api/assignments/worker/<worker_id>?scenario=<scenario_id>
```

**Response**:
```json
{
  "workerId": "Mechanic_1",
  "totalTasks": 15,
  "totalHours": 120.5,
  "utilization": 75.3,
  "tasks": [...]
}
```

---

#### Get Team Schedule
```http
GET /api/assignments/team/<team_name>?scenario=<scenario_id>
```

**Response**:
```json
{
  "teamName": "Assembly",
  "capacity": 4,
  "utilization": 82.1,
  "shifts": {...},
  "tasks": [...]
}
```

---

### Export Endpoints

#### Export Scenario Data
```http
GET /api/export/<scenario_id>?format=csv
```

**Response**: CSV file download

**Formats**:
- `csv`: Comma-separated values
- `excel`: Microsoft Excel (.xlsx)
- `json`: JSON format

---

### Supply Chain Endpoints

#### Get Product Status
```http
GET /api/supply-chain/product/<product_id>?scenario=<scenario_id>
```

**Response**:
```json
{
  "productId": "Product_A",
  "deliveryDate": "2025-11-15",
  "dueDate": "2025-11-10",
  "lateness": 5,
  "status": "late",
  "tasks": [...],
  "criticalPath": [...]
}
```

---

#### Get Late Parts Analysis
```http
GET /api/supply-chain/late-parts?scenario=<scenario_id>
```

**Response**:
```json
{
  "affectedProducts": 5,
  "totalDelay": 12.5,
  "lateParts": [
    {
      "partId": "Part_X",
      "expectedDate": "2025-10-20",
      "actualDate": "2025-10-23",
      "impactedProducts": [...]
    }
  ]
}
```

---

## ⚙️ Configuration

### Application Settings

Edit `src/app.py` to configure:

```python
app.config['JSON_AS_ASCII'] = False            # UTF-8 JSON encoding
app.config['TEMPLATES_AUTO_RELOAD'] = True     # Hot reload templates
app.config['SEND_FILE_MAX_AGE_DEFAULT'] = 0    # Disable caching
```

---

### Scheduler Parameters

Configure scheduler behavior in `src/scheduler/main.py`:

```python
scheduler = ProductionScheduler(
    csv_file='scheduling_data.csv',      # Input data file
    debug=False,                          # Enable debug logging
    late_part_delay_days=1.0,            # Late part impact (days)
    default_shift_hours=8.0,             # Work hours per shift
    quality_team_capacity={'QA': 2}      # Quality team size
)
```

---

### Optimization Settings

Adjust CP-SAT solver parameters:

```python
# In src/scheduler/cp_sat_solver.py
solver.parameters.max_time_in_seconds = 60        # Timeout
solver.parameters.num_search_workers = 8          # Parallel threads
solver.parameters.log_search_progress = True      # Verbose logging
```

---

### Data Loader Configuration

Customize CSV parsing in `src/scheduler/data_loader.py`:

```python
# Column name mappings
COLUMN_MAPPINGS = {
    'Task': 'task_name',
    'Product': 'product_id',
    'Duration (days)': 'duration',
    'Due Date': 'due_date',
    # ... more mappings
}

# Date format
DATE_FORMAT = '%Y-%m-%d'

# Missing value handling
FILL_NA_VALUES = {
    'duration': 1.0,
    'priority': 5
}
```

---

### Frontend Customization

Edit `static/css/dashboard.css` for styling:

```css
/* Brand colors */
:root {
    --primary-color: #2563eb;
    --secondary-color: #7c3aed;
    --success-color: #10b981;
    --warning-color: #f59e0b;
    --danger-color: #ef4444;
}

/* Layout settings */
.dashboard-container {
    max-width: 1400px;
    padding: 20px;
}
```

---

## 📁 Project Structure

```
FOCUS-feat-impact-analysis-dashboard-clean/
│
├── run.py                              # Application entry point
├── requirements.txt                    # Python dependencies
├── scheduling_data.csv                 # Input data file
├── .gitignore                         # Git ignore rules
├── README.md                          # This file
│
├── src/                               # Source code
│   ├── __init__.py                   # Package initializer
│   ├── app.py                        # Flask application factory
│   ├── exporter.py                   # Data export utilities
│   ├── server_utils.py               # Server helper functions
│   │
│   ├── blueprints/                   # Flask route modules
│   │   ├── main.py                  # Main routes (landing, dashboard)
│   │   ├── scenarios.py             # Scenario management routes
│   │   ├── assignments.py           # Worker/team assignment routes
│   │   ├── supply_chain.py          # Supply chain routes
│   │   └── industrial_engineering.py # IE analysis routes
│   │
│   └── scheduler/                    # Core scheduling engine
│       ├── __init__.py              # Scheduler package init
│       ├── main.py                  # ProductionScheduler class
│       ├── algorithms.py            # Scheduling algorithms
│       ├── cp_sat_solver.py         # OR-Tools integration
│       ├── constraints.py           # Constraint definitions
│       ├── data_loader.py           # CSV data parsing
│       ├── metrics.py               # Performance calculations
│       ├── scenarios.py             # Scenario management
│       ├── validation.py            # Schedule validation
│       ├── reporting.py             # Report generation
│       ├── utils.py                 # Utility functions
│       └── debug.py                 # Debugging tools
│
├── static/                           # Frontend assets
│   ├── css/
│   │   └── dashboard.css            # Main stylesheet
│   ├── images/
│   │   └── Negative-mask-effect.gif # Landing page animation
│   └── js/
│       └── dashboard-js.js          # Dashboard JavaScript
│
└── templates/                        # HTML templates
    ├── landing_page.html            # Entry page
    ├── dashboard2.html              # Main dashboard
    └── partials/                    # View components
        ├── _header.html
        ├── _management_view.html
        ├── _industrial_engineering_view.html
        ├── _supply_chain_view.html
        ├── _worker_gantt_view.html
        ├── _team_lead_view.html
        ├── _mechanic_view.html
        ├── _project_view.html
        ├── _scenario_view.html
        ├── _todo_view.html
        └── _worker_gantt_view.html
```

---

## 📊 Data Format

### Input CSV Structure

Your `scheduling_data.csv` should have the following columns:

```csv
Task,Product,Duration (days),Team,Predecessor,Due Date,Priority,Late Part Delay,Quality Team
Build_A_1,Product_A,3.0,Assembly,,2025-11-10,5,0.0,
Build_A_2,Product_A,2.5,Fabrication,Build_A_1,2025-11-10,5,0.0,
QA_A_1,Product_A,1.0,Quality,Build_A_2,2025-11-10,5,0.0,QA
Ship_A_1,Product_A,0.5,Shipping,QA_A_1,2025-11-10,5,0.0,
...
```

### Column Descriptions

| Column | Type | Required | Description |
|--------|------|----------|-------------|
| `Task` | string | ✅ Yes | Unique task identifier |
| `Product` | string | ✅ Yes | Product this task belongs to |
| `Duration (days)` | float | ✅ Yes | Task duration in work days |
| `Team` | string | ✅ Yes | Team responsible for task |
| `Predecessor` | string | ❌ No | Task that must complete first |
| `Due Date` | date | ✅ Yes | Product delivery deadline (YYYY-MM-DD) |
| `Priority` | int | ❌ No | Task priority (1-10, default: 5) |
| `Late Part Delay` | float | ❌ No | Delay due to late parts (days) |
| `Quality Team` | string | ❌ No | Quality team if task is QA |

### Data Validation Rules

1. **Task IDs**: Must be unique across all rows
2. **Products**: Multiple tasks can share same product
3. **Duration**: Must be > 0
4. **Dates**: Must be in YYYY-MM-DD format
5. **Predecessors**: Must reference existing task IDs
6. **Teams**: Should match available team names
7. **No Circular Dependencies**: Task A → B → C → A is invalid

### Example Data

```csv
Task,Product,Duration (days),Team,Predecessor,Due Date,Priority,Late Part Delay,Quality Team
Build_Widget_1,Widget_100,4.0,Assembly,,2025-12-15,7,0.0,
Paint_Widget_1,Widget_100,1.5,Paint,Build_Widget_1,2025-12-15,7,0.0,
QA_Widget_1,Widget_100,0.5,Quality,Paint_Widget_1,2025-12-15,7,0.0,QA
Pack_Widget_1,Widget_100,0.5,Packaging,QA_Widget_1,2025-12-15,7,0.0,
Ship_Widget_1,Widget_100,1.0,Shipping,Pack_Widget_1,2025-12-15,7,0.0,
```

### Generating Sample Data

Use the included data generator (if needed):

```python
from src.scheduler.utils import generate_sample_data

generate_sample_data(
    num_products=20,
    tasks_per_product=5,
    output_file='scheduling_data.csv'
)
```

---

## 🎭 Scenarios

### Baseline Scenario

**Description**: Current scheduling approach using global priority list

**Method**: Heuristic task prioritization with greedy assignment

**Characteristics**:
- Fast computation (< 1 second)
- Uses existing team capacities
- Allows late deliveries with penalties
- Good for quick daily planning

**When to Use**:
- Daily operations
- Quick what-if analysis
- Initial planning

---

### Scenario 1: CSV Headcount Optimization

**Description**: Optimizes workforce size based on CSV configuration

**Method**: Capacity adjustment + priority scheduling

**Characteristics**:
- Adjusts team sizes to meet demand
- Balances workload across teams
- Maintains priority-based scheduling
- Moderate computation time (1-5 seconds)

**When to Use**:
- Capacity planning
- Staffing decisions
- Budget analysis

**Configuration**:
```python
result = scheduler.scenario_1_csv_headcount()
```

---

### Scenario 3: Full CP-SAT Optimization

**Description**: Mathematical optimization for minimum makespan

**Method**: Constraint programming with OR-Tools CP-SAT

**Characteristics**:
- Finds optimal or near-optimal solution
- Minimizes total completion time
- Calculates minimum required workforce
- Longer computation (10-60 seconds)

**When to Use**:
- Strategic planning
- Proof of concept
- Maximum efficiency analysis

**Configuration**:
```python
result = scheduler.scenario_3_optimal_schedule(
    max_solve_time_seconds=60,
    num_workers=None  # Auto-calculate minimum
)
```

---

### Comparing Scenarios

Use the Scenario View to compare:

1. Navigate to **Scenarios** tab
2. Select product to prioritize (optional)
3. Click **"Run Prioritization Scenario"**
4. Review comparison table:
   - Makespan differences
   - On-time delivery changes
   - Workforce requirements
   - Resource utilization

---

## 🛠️ Development

### Setting Up Development Environment

```bash
# Clone repository
git clone https://github.com/yourusername/FOCUS-dashboard.git
cd FOCUS-dashboard

# Create virtual environment
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows

# Install dependencies
pip install -r requirements.txt

# Install development dependencies (optional)
pip install pytest pytest-cov black flake8 mypy
```

---

### Running in Development Mode

```bash
# Enable debug mode
export FLASK_ENV=development  # Linux/macOS
set FLASK_ENV=development     # Windows

# Run with auto-reload
python run.py
```

Flask will now reload automatically when you edit files.

---

### Code Style

This project follows PEP 8 style guidelines:

```bash
# Format code with Black
black src/

# Check style with flake8
flake8 src/ --max-line-length=100

# Type checking with mypy
mypy src/
```

---

### Adding New Views

1. **Create template** in `templates/partials/`:
```html
<!-- _my_new_view.html -->
<div id="my-view" class="view-content" style="display: none;">
    <h2>My New View</h2>
    <!-- Your content -->
</div>
```

2. **Add to dashboard template** (`templates/dashboard2.html`):
```html
{% include 'partials/_my_new_view.html' %}
```

3. **Add JavaScript handler** in `static/js/dashboard-js.js`:
```javascript
function showMyView() {
    hideAllViews();
    document.getElementById('my-view').style.display = 'block';
    loadMyViewData();
}

function loadMyViewData() {
    fetch('/api/my-endpoint')
        .then(response => response.json())
        .then(data => {
            // Populate view with data
        });
}
```

4. **Add API endpoint** in `src/blueprints/`:
```python
@my_bp.route('/api/my-endpoint')
def my_endpoint():
    # Your logic here
    return jsonify(result)
```

---

### Adding New Scenarios

1. **Implement scenario method** in `src/scheduler/scenarios.py`:
```python
def scenario_4_custom_optimization(self, **kwargs):
    """
    Custom optimization scenario
    """
    # Your optimization logic
    return result
```

2. **Add to scenario runner** in `src/app.py`:
```python
# Run scenario 4
result4 = scheduler.scenario_4_custom_optimization()
scenario_results['scenario4'] = export_scenario_with_capacities(
    scheduler, 'scenario4'
)
```

3. **Update frontend** to display new scenario in selector

---

## 🧪 Testing

### Running Tests

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=src --cov-report=html

# Run specific test file
pytest tests/test_scheduler.py

# Run specific test
pytest tests/test_scheduler.py::test_load_data
```

---

### Test Structure

```
tests/
├── __init__.py
├── test_scheduler.py          # Scheduler engine tests
├── test_algorithms.py         # Algorithm tests
├── test_constraints.py        # Constraint validation tests
├── test_api.py               # API endpoint tests
└── fixtures/
    └── test_data.csv         # Sample test data
```

---

### Writing Tests

Example test:

```python
import pytest
from src.scheduler.main import ProductionScheduler

def test_scheduler_initialization():
    scheduler = ProductionScheduler('tests/fixtures/test_data.csv')
    scheduler.load_data_from_csv()
    assert len(scheduler.tasks) > 0
    assert scheduler.products is not None

def test_baseline_scheduling():
    scheduler = ProductionScheduler('tests/fixtures/test_data.csv')
    scheduler.load_data_from_csv()
    scheduler.generate_global_priority_list()
    
    # Verify all tasks are scheduled
    assert all(task.start is not None for task in scheduler.tasks)
    
    # Verify no capacity violations
    # ... more assertions
```

---

## 🚀 Deployment

### Production Considerations

1. **Use Production WSGI Server** (not Flask's built-in server):
```bash
pip install gunicorn
gunicorn -w 4 -b 0.0.0.0:5000 "src.app:create_app()"
```

2. **Set Environment Variables**:
```bash
export FLASK_ENV=production
export SECRET_KEY=your-secret-key-here
```

3. **Enable HTTPS** with nginx/Apache reverse proxy

4. **Configure Logging**:
```python
import logging
logging.basicConfig(level=logging.INFO)
```

5. **Use Process Manager** (systemd, supervisor, pm2)

---

### Docker Deployment

Create `Dockerfile`:

```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 5000

CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:5000", "src.app:create_app()"]
```

Build and run:
```bash
docker build -t focus-dashboard .
docker run -p 5000:5000 focus-dashboard
```

---

### Cloud Deployment

#### Heroku

```bash
# Create Procfile
echo "web: gunicorn -w 4 -b 0.0.0.0:\$PORT 'src.app:create_app()'" > Procfile

# Deploy
heroku create focus-dashboard
git push heroku main
```

#### AWS Elastic Beanstalk

```bash
eb init -p python-3.9 focus-dashboard
eb create focus-prod
eb deploy
```

#### Google Cloud Run

```bash
gcloud run deploy focus-dashboard \
  --source . \
  --platform managed \
  --region us-central1 \
  --allow-unauthenticated
```

---

## 🐛 Troubleshooting

### Common Issues

#### Issue: OR-Tools Installation Fails

**Solution**:
```bash
# Try upgrading pip first
pip install --upgrade pip

# Install with specific version
pip install ortools==9.14.6206

# If still fails, try conda:
conda install -c conda-forge ortools-python
```

---

#### Issue: Port 5000 Already in Use

**Solution**:
```bash
# Find process using port 5000
# Linux/macOS:
lsof -i :5000
kill -9 <PID>

# Windows:
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# Or change port in run.py:
app.run(debug=True, host='0.0.0.0', port=8080)
```

---

#### Issue: CSV File Not Found

**Error**: `FileNotFoundError: scheduling_data.csv`

**Solution**:
1. Ensure file is in project root directory
2. Check file name matches exactly (case-sensitive)
3. Verify path in `src/app.py`:
```python
scheduler = ProductionScheduler('scheduling_data.csv')
```

---

#### Issue: Scenario 3 Takes Too Long

**Solution**:
1. Reduce solve time limit:
```python
result = scheduler.scenario_3_optimal_schedule(
    max_solve_time_seconds=30  # Reduce from 60
)
```

2. Reduce problem size by filtering data
3. Use scenario 1 instead for faster results

---

#### Issue: Memory Error with Large Datasets

**Solution**:
1. Increase system memory
2. Reduce dataset size
3. Implement data pagination:
```python
# Limit to top 1000 tasks
scheduler.tasks = scheduler.tasks[:1000]
```

---

#### Issue: Blank Dashboard Page

**Solution**:
1. Check browser console for JavaScript errors (F12)
2. Verify API endpoints are returning data:
```bash
curl http://localhost:5000/api/scenarios/baseline
```
3. Clear browser cache (Ctrl+Shift+Delete)
4. Check Flask logs for errors

---

### Debug Mode

Enable detailed logging:

```python
# In src/scheduler/main.py
scheduler = ProductionScheduler(
    'scheduling_data.csv',
    debug=True  # Enable debug mode
)
```

View logs:
```bash
# In terminal where you ran python run.py
# Look for DEBUG messages
```

---

### Getting Help

1. **Check Documentation**: Review this README and inline code comments
2. **Search Issues**: GitHub Issues page for similar problems
3. **Enable Debug Logging**: Set `debug=True` to see detailed output
4. **Minimum Reproducible Example**: Create small test case that shows the problem
5. **Ask for Help**: Open GitHub issue with:
   - Steps to reproduce
   - Expected vs actual behavior
   - Error messages
   - System information

---

## ⚡ Performance

### Optimization Tips

1. **Reduce Dataset Size**: Filter unnecessary tasks/products
2. **Adjust Time Limits**: Balance quality vs speed
3. **Use Caching**: Cache scenario results
4. **Parallel Processing**: Enable multi-threading in CP-SAT
5. **Database Backend**: For large datasets, use PostgreSQL

### Benchmarks

Typical performance on modern hardware (Intel i5/Ryzen 5, 16GB RAM):

| Dataset Size | Baseline | Scenario 1 | Scenario 3 |
|-------------|----------|------------|------------|
| 50 tasks | < 0.1s | 0.5s | 2-5s |
| 100 tasks | 0.2s | 1s | 5-15s |
| 200 tasks | 0.5s | 2s | 15-30s |
| 500 tasks | 1s | 5s | 30-60s |

---

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

### How to Contribute

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/my-new-feature`
3. **Make your changes**
4. **Add tests** for new functionality
5. **Run tests**: `pytest`
6. **Commit changes**: `git commit -am 'Add new feature'`
7. **Push to branch**: `git push origin feature/my-new-feature`
8. **Submit Pull Request**

### Contribution Guidelines

- Follow PEP 8 style guidelines
- Add docstrings to all functions/classes
- Write unit tests for new code
- Update documentation as needed
- Keep commits atomic and well-described

### Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Focus on the issue, not the person
- Accept constructive criticism gracefully

---

## 📄 License

This project is licensed under the MIT License - see below for details:

```
MIT License

Copyright (c) 2025 FOCUS Production Scheduling Dashboard

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🙏 Acknowledgments

### Technologies

- **Google OR-Tools**: Constraint programming solver
- **Flask**: Web framework
- **Pandas**: Data manipulation library
- **Chart.js**: Visualization library (if used)

### Inspiration

This project was inspired by real-world manufacturing scheduling challenges and the need for accessible optimization tools.

### Contributors

Thank you to all contributors who have helped improve this project!

---

## 📞 Contact & Support

- **Issues**: [GitHub Issues](https://github.com/yourusername/FOCUS-dashboard/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/FOCUS-dashboard/discussions)
- **Email**: your.email@example.com

---

## 🗺️ Roadmap

### Upcoming Features

- [ ] Real-time scheduling updates
- [ ] Machine learning-based duration predictions
- [ ] Multi-site scheduling support
- [ ] Mobile app for shop floor
- [ ] Integration with ERP systems (SAP, Oracle)
- [ ] Advanced resource leveling
- [ ] Stochastic optimization
- [ ] Automated report generation
- [ ] Custom constraint builder UI
- [ ] Multi-user collaboration

### Future Enhancements

- Database backend (PostgreSQL/MongoDB)
- WebSocket support for live updates
- REST API documentation with Swagger
- Docker Compose for easy deployment
- Kubernetes deployment configs
- CI/CD pipeline with GitHub Actions
- Internationalization (i18n) support
- Dark mode theme
- Export to MS Project/Primavera

---

## 📚 Additional Resources

### Documentation

- [Google OR-Tools Documentation](https://developers.google.com/optimization)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [Pandas Documentation](https://pandas.pydata.org/docs/)

### Tutorials

- [Constraint Programming Tutorial](https://developers.google.com/optimization/cp)
- [Production Scheduling Basics](https://example.com/scheduling-101)
- [OR-Tools CP-SAT Examples](https://github.com/google/or-tools/tree/stable/examples/python)

### Research Papers

- "Constraint Programming for Scheduling" - Handbook of Constraint Programming
- "Job Shop Scheduling with OR-Tools" - Google AI Blog
- "Production Scheduling in Industry 4.0" - IEEE Transactions

---

<div align="center">

**Made with ❤️ for better production planning**

[⬆ Back to Top](#focus-production-scheduling-dashboard)

</div>
