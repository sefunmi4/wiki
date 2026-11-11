# Platform UI/UX Design Specifications (Claude Design System)

## Overview
Derived from the latest Claude Design iterations, this document outlines the core panel structures and interactive workflows across the **E-CO**, **Ethos**, **ECHO**, and **Architecture of Homo Sapiens** platforms.

## Core Expanded View Panels

### 1. Free Speech Expanded View Panel
* **Layout:** Displays rich post details with a clean truncation/collapse mechanism (`...`).
* **Navigation:** Direct routing to dedicated standalone post and thread detail pages.

### 2. File Expanded View Panel
* **Layout:** A read-only vertical scrollable view featuring faint line numbers at the left margin (modeled after an A4 piece of paper in detailed view).
* **Controls:** Dynamic permissions-based editing and version tracking.

### 3. Task Expanded View Panel
* **Layout:** Split-panel interface.
  * *Left Panel:* Hierarchical folder tree view.
  * *Right Panel:* Tabbed interface containing **Planner** (Kanban board with columns for *Todo, In Progress, Requested, In Review, and Done* supporting drag-and-drop state triggers) and **Options** (team member invitations, role requests, and privacy toggles).

### 4. Project Expanded View Panel
* **Layout:** Split-panel interface.
  * *Left Panel:* Interactive graph view mapping node dependencies and connections.
  * *Right Panel:* Tabbed interface containing **Folders** (folder/task/subtask/file structures) and **Options** controls.
