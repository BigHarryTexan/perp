> **Public Notice:**  
> This file defines the *structure* of the Perpetual Résumé system.  
> It contains **no personal, private, or proprietary career data**.  
> All real résumé content should be stored in a **separate private repository**.  
> This schema is safe for public use, open-source collaboration, and long-term evolution.
# Perpetual Résumé schema

This document defines the core data model for the Perpetual Résumé (“Perp”).  
Goal: make a person’s career, skills, and work artifacts queryable, composable, and evergreen.

---

## 1. Person

- **id**: string (UUID or slug)
- **full_name**: string
- **tagline**: string (short “who I am” line)
- **location**: string
- **email**: string
- **links**: array of Link
- **summary**: string (narrative overview)
- **current_focus**: string (what they’re optimizing for now)

### Link

- **label**: string (e.g., “LinkedIn”, “GitHub”, “Portfolio”)
- **url**: string

---

## 2. Experience

Represents roles, contracts, or engagements.

- **id**: string
- **person_id**: string (FK → Person.id)
- **organization**: string
- **role_title**: string
- **employment_type**: enum  
  - `full_time` | `part_time` | `contract` | `consulting` | `fractional` | `other`
- **location**: string
- **remote_status**: enum  
  - `onsite` | `hybrid` | `remote`
- **start_date**: date (YYYY-MM)
- **end_date**: date or `null` (for current)
- **is_current**: boolean
- **summary**: string (1–3 sentence overview)
- **highlights**: array of Highlight
- **skills_used**: array of SkillRef
- **outcomes**: array of Outcome

### Highlight

- **id**: string
- **experience_id**: string
- **text**: string (bullet-level detail)
- **impact_level**: enum  
  - `low` | `medium` | `high`
- **tags**: array of string (e.g., `["leadership", "migration", "SLA"]`)

### Outcome

- **id**: string
- **experience_id**: string
- **description**: string
- **metric**: string (e.g., “MTTR”, “CSAT”, “Revenue”)
- **value**: string (e.g., “+18%”, “-32%”, “$1.2M”)
- **timeframe**: string (e.g., “6 months”, “Q3 2024”)

---

## 3. Skills

Canonical skill inventory, decoupled from any single job.

- **id**: string
- **name**: string (e.g., “Change Management”, “Incident Management”)
- **category**: string (e.g., “Leadership”, “Technical”, “Domain”)
- **proficiency**: enum  
  - `familiar` | `proficient` | `advanced` | `expert`
- **years_experience**: number
- **last_used**: date (YYYY-MM)
- **evidence**: array of EvidenceRef

### SkillRef

- **skill_id**: string
- **context**: string (e.g., “Primary skill in this role”)

### EvidenceRef

- **source_type**: enum  
  - `experience` | `project` | `artifact`
- **source_id**: string
- **note**: string

---

## 4. Projects

Cross-cutting work that may span multiple roles.

- **id**: string
- **person_id**: string
- **name**: string
- **role**: string (e.g., “Lead”, “Contributor”)
- **start_date**: date
- **end_date**: date or `null`
- **summary**: string
- **technologies**: array of string
- **skills_used**: array of SkillRef
- **outcomes**: array of Outcome
- **links**: array of Link

---

## 5. Artifacts

Concrete things someone can point to.

- **id**: string
- **person_id**: string
- **title**: string
- **type**: enum  
  - `document` | `deck` | `repo` | `talk` | `article` | `other`
- **description**: string
- **url**: string
- **related_experience_ids**: array of string
- **related_project_ids**: array of string

---

## 6. Views

Predefined “lenses” over the data (for UI or exports).

- **id**: string
- **name**: string (e.g., “Executive Summary”, “Technical Deep Dive”)
- **description**: string
- **filters**: JSON (criteria on experiences, skills, projects)
- **sort_order**: JSON (e.g., by impact, recency)
- **layout_hint**: string (e.g., “one-page”, “narrative”, “timeline”)

---

## 7. Metadata

- **schema_version**: string (e.g., `1.0.0`)
- **last_updated**: datetime
- **owner**: string (person_id or slug)
