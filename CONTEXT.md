# Educational Website & VLE Platform Project

## PROJECT_METADATA
```json
{
  "project_name": "Educational Website with VLE Platform",
  "project_type": "web_application",
  "project_category": "education",
  "primary_audience": ["students", "educators", "administrators"],
  "project_scale": "medium_to_large",
  "estimated_timeline_weeks": "28-42"
}
```

## DEPLOYMENT_INFRASTRUCTURE
```json
{
  "environments": [
    {
      "name": "development",
      "purpose": "Local development and testing",
      "infrastructure": "Docker containers on developer machines",
      "database": "Local PostgreSQL instance",
      "features": ["hot-reloading", "debug tools", "test data generation"]
    },
    {
      "name": "staging",
      "purpose": "Integration testing and QA",
      "infrastructure": "DigitalOcean Droplets (Standard instances)",
      "scaling": "Fixed instances behind load balancer",
      "database": "DigitalOcean MySQL Database (medium instance)",
      "caching": "Redis (t3.small instance)",
      "features": ["staging-only analytics", "anonymized production data"]
    },
    {
      "name": "production",
      "purpose": "Live application",
      "infrastructure": "DigitalOcean Droplets (CPU-Optimized instances with autoscaling)",
      "scaling": "Auto-scaling based on CPU and memory metrics",
      "database": {
        "primary": "DigitalOcean MySQL Database (large instance)",
        "read_replicas": 2,
        "backup_frequency": "hourly"
      },
      "caching": {
        "service": "DigitalOcean Redis Database",
        "clustering": true,
        "ttl_defaults": {
          "page_cache": 3600,
          "api_responses": 300,
          "user_sessions": 86400
        }
      },
      "cdn": {
        "provider": "Cloudflare",
        "cached_content": ["static assets", "media files", "public pages"]
      },
      "monitoring": {
        "services": ["DigitalOcean Monitoring", "Datadog", "Uptime Robot"],
        "alert_channels": ["email", "SMS", "Slack"]
      }
    }
  ],
  "ci_cd_pipeline": {
    "source_control": "GitHub",
    "ci_service": "GitHub Actions",
    "workflow_triggers": {
      "pull_request": ["lint", "unit tests", "build verification"],
      "merge_to_develop": ["integration tests", "staging deployment"],
      "merge_to_main": ["production deployment"]
    },
    "testing_strategy": {
      "unit_testing": {
        "frontend": "Jest + React Testing Library",
        "backend": "Jest + Supertest"
      },
      "integration_testing": "Cypress",
      "performance_testing": "k6",
      "security_testing": "OWASP ZAP"
    },
    "deployment_process": {
      "build_artifacts": "Docker images stored in Docker Hub",
      "database_migrations": "Sequelize migrations run before deployment",
      "deployment_strategy": "Blue-green deployment",
      "rollback_capability": true
    }
  },
  "disaster_recovery": {
    "rpo_hours": 1,
    "rto_hours": 4,
    "backup_strategy": {
      "database": "Point-in-time recovery with transaction logs",
      "file_storage": "DigitalOcean Spaces with backup retention policy",
      "system_configuration": "Infrastructure as Code (Terraform)"
    },
    "failover_strategy": "Multi-AZ deployment with automated failover"
  },
  "scaling_plan": {
    "initial_capacity": {
      "concurrent_users": 500,
      "course_capacity": 200,
      "storage_gb": 500
    },
    "target_capacity": {
      "year_1": {
        "concurrent_users": 2000,
        "course_capacity": 500,
        "storage_gb": 2000
      },
      "year_2": {
        "concurrent_users": 5000,
        "course_capacity": 1000,
        "storage_gb": 5000
      }
    },
    "scaling_strategy": "Horizontal scaling with microservices evolution"
  }
}
```

## MAINTENANCE_PLAN
```json
{
  "routine_maintenance": {
    "security_updates": {
      "frequency": "weekly",
      "process": "Automated scanning and patching with manual verification"
    },
    "database_optimization": {
      "frequency": "monthly",
      "tasks": ["index optimization", "query performance analysis", "storage reclamation"]
    },
    "backup_verification": {
      "frequency": "weekly",
      "process": "Automated restore testing to staging environment"
    }
  },
  "monitoring": {
    "uptime_monitoring": {
      "endpoints": [
        {"name": "public_website", "sla_percentage": 99.9},
        {"name": "vle_platform", "sla_percentage": 99.5},
        {"name": "api_services", "sla_percentage": 99.9}
      ],
      "alert_thresholds": {
        "response_time_ms": 500,
        "error_rate_percentage": 1.0
      }
    },
    "performance_monitoring": {
      "metrics": [
        {"name": "page_load_time", "threshold_ms": 1500},
        {"name": "api_response_time", "threshold_ms": 300},
        {"name": "database_query_time", "threshold_ms": 100},
        {"name": "cpu_utilization", "threshold_percentage": 70},
        {"name": "memory_utilization", "threshold_percentage": 80}
      ]
    },
    "usage_analytics": {
      "metrics": [
        "daily_active_users",
        "course_enrollment_rate",
        "content_engagement_time",
        "assignment_completion_rate",
        "user_retention_rate"
      ],
      "reporting_frequency": "weekly"
    }
  },
  "update_schedule": {
    "major_releases": {
      "frequency": "quarterly",
      "scope": "New features and significant improvements",
      "deployment_window": "Weekend, off-peak hours"
    },
    "minor_releases": {
      "frequency": "monthly",
      "scope": "Bug fixes and minor enhancements",
      "deployment_window": "Weeknight, off-peak hours"
    },
    "hotfixes": {
      "criteria": "Critical bugs and security vulnerabilities",
      "approval_process": "Emergency change approval",
      "deployment": "As needed with minimal disruption"
    }
  },
  "support_plan": {
    "tiers": [
      {
        "name": "student_support",
        "channels": ["email", "knowledge base", "community forums"],
        "response_time_hours": 24,
        "hours": "Monday-Friday, 9am-5pm"
      },
      {
        "name": "instructor_support",
        "channels": ["email", "chat", "knowledge base"],
        "response_time_hours": 8,
        "hours": "Monday-Friday, 9am-7pm"
      },
      {
        "name": "admin_support",
        "channels": ["email", "chat", "phone", "dedicated agent"],
        "response_time_hours": 4,
        "hours": "24/7"
      }
    ],
    "knowledge_base": {
      "sections": [
        "getting_started",
        "student_guides",
        "instructor_guides",
        "administrator_guides",
        "troubleshooting",
        "faq"
      ],
      "update_frequency": "monthly"
    }
  }
}
```

## TESTING_STRATEGY
```json
{
  "testing_levels": {
    "unit_testing": {
      "coverage_target_percentage": 80,
      "focus_areas": [
        "core business logic",
        "data validation",
        "authentication/authorization",
        "critical user flows"
      ],
      "tools": {
        "frontend": "Jest, React Testing Library",
        "backend": "Jest, Supertest"
      }
    },
    "integration_testing": {
      "focus_areas": [
        "API contract validation",
        "database interactions",
        "third-party service integrations",
        "cross-component workflows"
      ],
      "tools": ["Cypress", "Postman/Newman"]
    },
    "end_to_end_testing": {
      "critical_flows": [
        "user registration and login",
        "course enrollment and payment",
        "content access and progress tracking",
        "assignment submission and grading",
        "discussion participation"
      ],
      "tools": ["Cypress", "Selenium"]
    },
    "performance_testing": {
      "scenarios": [
        {
          "name": "concurrent_user_load",
          "users": 500,
          "duration_minutes": 30,
          "acceptance_criteria": {
            "average_response_time_ms": 500,
            "95th_percentile_response_time_ms": 1500,
            "error_rate_percentage": 1
          }
        },
        {
          "name": "database_load",
          "simulated_records": {
            "courses": 1000,
            "users": 10000,
            "enrollments": 50000
          },
          "acceptance_criteria": {
            "query_performance_degradation_percentage": 20
          }
        }
      ],
      "tools": ["k6", "JMeter"]
    },
    "security_testing": {
      "types": [
        "vulnerability scanning",
        "penetration testing",
        "dependency analysis",
        "authentication/authorization testing"
      ],
      "frequency": "quarterly",
      "tools": ["OWASP ZAP", "Snyk", "SonarQube"]
    },
    "accessibility_testing": {
      "standards": "WCAG 2.1 AA",
      "testing_methods": [
        "automated scanning",
        "screen reader testing",
        "keyboard navigation testing"
      ],
      "tools": ["axe", "WAVE", "Lighthouse"]
    }
  },
  "testing_environments": {
    "development": {
      "purpose": "Developer testing",
      "data": "Synthetic test data",
      "refresh_frequency": "On demand"
    },
    "staging": {
      "purpose": "Pre-release verification",
      "data": "Anonymized production data",
      "refresh_frequency": "Weekly"
    },
    "production": {
      "purpose": "Post-deployment verification",
      "testing_limitations": "Non-disruptive smoke tests only"
    }
  },
  "test_automation": {
    "ci_integration": {
      "unit_tests": "Run on every PR",
      "integration_tests": "Run on merge to develop",
      "e2e_tests": "Run on release candidate builds"
    },
    "test_data_management": {
      "approach": "Seed data generation scripts",
      "data_refresh_strategy": "Reset before each test suite"
    },
    "reporting": {
      "metrics": [
        "test coverage percentage",
        "pass/fail rates",
        "test execution time"
      ],
      "visualization": "Dashboard in CI/CD pipeline"
    }
  },
  "quality_gates": [
    {
      "stage": "code_review",
      "criteria": [
        "All unit tests passing",
        "Code coverage meets targets",
        "No critical or high security vulnerabilities",
        "Code quality standards met"
      ]
    },
    {
      "stage": "staging_deployment",
      "criteria": [
        "All integration tests passing",
        "All e2e tests passing",
        "Performance tests meet acceptance criteria",
        "No accessibility violations"
      ]
    },
    {
      "stage": "production_deployment",
      "criteria": [
        "Staging environment smoke tests passing",
        "UAT sign-off received",
        "Security scan completed",
        "Rollback plan verified"
      ]
    }
  ]
}
```

## OBJECTIVES
```json
[
  {
    "id": "obj_1",
    "description": "Create an engaging public-facing website to showcase courses",
    "priority": "high"
  },
  {
    "id": "obj_2",
    "description": "Develop a secure VLE with student authentication and profiles",
    "priority": "high"
  },
  {
    "id": "obj_3",
    "description": "Integrate with third-party teaching platforms",
    "priority": "medium"
  },
  {
    "id": "obj_4",
    "description": "Provide intuitive navigation between public and private sections",
    "priority": "medium"
  },
  {
    "id": "obj_5",
    "description": "Ensure responsive design across all devices",
    "priority": "high"
  }
]
```

## TECH_STACK_OVERVIEW
```
The technology stack has been chosen to balance ease of use for developers with limited 
experience while ensuring scalability and maintainability. Alternative options are provided 
for both database and hosting infrastructure to match different experience levels and budget constraints.
```

## UI_DESIGN_SYSTEM
```json
{
  "color_scheme": {
    "primary": {
      "name": "Educational-Focused Color Palette",
      "colors": {
        "primary": "#4361EE",
        "secondary": "#3F8EFC",
        "accent": "#F72585",
        "success": "#4CAF50",
        "warning": "#FF9800",
        "error": "#F44336",
        "neutral": {
          "white": "#FFFFFF",
          "light_gray": "#F5F7FA",
          "medium_gray": "#E1E5EB",
          "dark_gray": "#6B7280",
          "near_black": "#1F2937"
        }
      },
      "usage": {
        "primary": "Buttons, links, and primary actions",
        "secondary": "Secondary elements and highlights",
        "accent": "Calls-to-action and important elements",
        "success": "Completion and success indicators",
        "warning": "Alerts and warnings",
        "error": "Errors and critical notifications",
        "white": "Background",
        "light_gray": "Secondary background",
        "medium_gray": "Borders",
        "dark_gray": "Secondary text",
        "near_black": "Primary text"
      }
    },
    "alternative": {
      "name": "Calm Learning Environment",
      "colors": {
        "primary": "#34BE82",
        "secondary": "#81B29A",
        "accent": "#F9C74F",
        "text": "#2D3748",
        "background": "#F7F9FC"
      }
    }
  },
  "typography": {
    "font_families": {
      "headings": "Poppins, sans-serif",
      "body": "Inter, sans-serif",
      "accents": "Georgia, serif",
      "monospace": "JetBrains Mono, monospace"
    },
    "font_sizes": {
      "h1": "2.5rem",
      "h2": "2rem",
      "h3": "1.5rem",
      "h4": "1.25rem",
      "body": "1rem",
      "small": "0.875rem"
    },
    "line_heights": {
      "headings": "1.2",
      "body": "1.5",
      "tight": "1.1",
      "loose": "1.8"
    }
  },
  "ui_components": {
    "navigation": [
      {
        "name": "Smart Sticky Header",
        "description": "Collapses to minimal version on scroll",
        "features": [
          "Contains logo, main navigation, search, and user profile",
          "Changes appearance between public site and VLE"
        ]
      },
      {
        "name": "Sidebar Navigation",
        "description": "Collapsible sidebar with course structure",
        "features": [
          "Visual progress indicators",
          "Quick access to important course elements"
        ]
      },
      {
        "name": "Breadcrumb Navigation",
        "description": "Contextual awareness within course content",
        "features": [
          "Easy navigation to parent sections"
        ]
      }
    ],
    "content_containers": [
      {
        "name": "Course Cards",
        "description": "Consistent card design with course information",
        "elements": [
          "Course thumbnail/image",
          "Title and short description",
          "Instructor avatar and name",
          "Progress bar (for enrolled courses)",
          "Duration and difficulty indicators",
          "Hover effects with quick actions"
        ]
      },
      {
        "name": "Content Modules",
        "description": "Expandable/collapsible sections",
        "elements": [
          "Clear visual hierarchy",
          "Progress indicators",
          "Completion checkmarks"
        ]
      },
      {
        "name": "Dashboard Widgets",
        "description": "Information blocks for the student dashboard",
        "elements": [
          "Recent activity timeline",
          "Upcoming deadlines calendar",
          "Achievement showcases",
          "Personalized recommendations"
        ]
      }
    ],
    "interactive_elements": [
      {
        "name": "Custom Video Player",
        "features": [
          "Branded appearance",
          "Playback speed controls",
          "Caption toggle",
          "Note-taking integration",
          "Timestamp bookmarking"
        ]
      },
      {
        "name": "Interactive Quizzes",
        "features": [
          "Multiple question types (MCQ, fill-in-blank, matching)",
          "Immediate feedback animations",
          "Progress tracking",
          "Review mode"
        ]
      },
      {
        "name": "Discussion Forums",
        "features": [
          "Threaded conversations",
          "Rich text formatting",
          "@mentions for students/instructors",
          "Upvoting system",
          "Instructor highlight badges"
        ]
      },
      {
        "name": "Assignment Submission",
        "features": [
          "Drag-and-drop file uploads",
          "Progress indicators",
          "Revision history",
          "Submission confirmation animations"
        ]
      }
    ],
    "feedback_elements": [
      {
        "name": "Toast Notifications",
        "description": "Non-intrusive corner notifications",
        "features": [
          "Color-coded by type (info, success, warning, error)",
          "Auto-dismiss with manual close option"
        ]
      },
      {
        "name": "Progress Visualization",
        "description": "Visual indicators of learning progress",
        "features": [
          "Circular progress charts for overall completion",
          "Linear progress bars for individual modules",
          "Achievement badges and milestones"
        ]
      },
      {
        "name": "Feedback Dialogs",
        "description": "Interactive feedback for user actions",
        "features": [
          "Animated reactions for correct/incorrect answers",
          "Celebratory animations for achievements",
          "Encouraging messages for progress milestones"
        ]
      }
    ]
  },
  "microinteractions": [
    {
      "name": "Course Enrollment Flow",
      "description": "Multi-step enrollment process with progress indicator",
      "elements": [
        "Confetti animation upon successful enrollment",
        "Welcome sequence introducing course features"
      ]
    },
    {
      "name": "Learning Path Visualization",
      "description": "Interactive roadmap of course content",
      "elements": [
        "Animated transitions between modules",
        "Visual cues for prerequisites and dependencies"
      ]
    },
    {
      "name": "Subtle UI Feedback",
      "description": "Microinteractions for user actions",
      "elements": [
        "Button state changes (hover, active, disabled)",
        "Form field validation indicators",
        "Page transition effects",
        "Loading states (skeleton screens instead of spinners)"
      ]
    }
  ],
  "accessibility": [
    {
      "name": "High Contrast Mode",
      "features": [
        "Alternative color scheme for better contrast",
        "Larger text option",
        "Increased spacing between elements"
      ]
    },
    {
      "name": "Screen Reader Optimizations",
      "features": [
        "Proper ARIA labels and roles",
        "Logical tab order",
        "Keyboard shortcuts for common actions"
      ]
    },
    {
      "name": "Focus Indicators",
      "features": [
        "Clear visual indicators for keyboard navigation",
        "Skip navigation links for keyboard users"
      ]
    }
  ],
  "mobile_elements": [
    {
      "name": "Bottom Navigation Bar",
      "features": [
        "Quick access to essential functions",
        "Active state indicators",
        "Haptic feedback"
      ]
    },
    {
      "name": "Pull-to-Refresh",
      "features": [
        "Custom animation tied to brand",
        "Visual feedback during content loading"
      ]
    },
    {
      "name": "Floating Action Buttons",
      "features": [
        "For primary actions like 'Continue Learning'",
        "Context-sensitive based on current screen"
      ]
    }
  ],
  "content_presentation": [
    {
      "name": "Rich Media Embeds",
      "features": [
        "Consistent styling for various media types",
        "Interactive infographics",
        "Embedded quizzes within content",
        "Code samples with syntax highlighting"
      ]
    },
    {
      "name": "Split View for Resources",
      "features": [
        "Side-by-side view of video and notes",
        "Synchronization between video timestamps and notes"
      ]
    },
    {
      "name": "Interactive Glossary",
      "features": [
        "Hover tooltips for technical terms",
        "Quick-access glossary sidebar"
      ]
    }
  ],
  "dashboard_elements": [
    {
      "name": "Learning Analytics",
      "features": [
        "Time spent visualizations",
        "Strength/weakness analysis",
        "Comparison to course averages (anonymized)",
        "Study streak calendar"
      ]
    },
    {
      "name": "Achievement System",
      "features": [
        "Badge showcase",
        "Progress milestones",
        "Skill tree visualization",
        "Unlockable features"
      ]
    },
    {
      "name": "Personalization Zone",
      "features": [
        "Custom theme options",
        "Content preference settings",
        "Learning pace adjustments",
        "Notification configuration"
      ]
    }
  ],
  "implementation_options": {
    "design_system": {
      "tools": ["Figma", "Storybook"],
      "deliverables": [
        "Component library",
        "Style guide",
        "Documentation"
      ]
    },
    "ui_frameworks": [
      {
        "name": "Material UI",
        "strengths": [
          "Comprehensive component library",
          "Well-documented",
          "Works well with React",
          "Highly customizable"
        ]
      },
      {
        "name": "Tailwind CSS",
        "strengths": [
          "Utility-first approach",
          "Rapid development",
          "Highly customizable",
          "Great for responsive design"
        ]
      },
      {
        "name": "Chakra UI",
        "strengths": [
          "Accessibility focused",
          "Composable components",
          "Easy theming",
          "Modern design aesthetic"
        ]
      }
    ],
    "animation_libraries": [
      "Framer Motion",
      "GSAP",
      "Lottie"
    ],
    "icon_sets": [
      "Phosphor Icons",
      "Heroicons",
      "Custom education icons"
    ]
  },
  "unique_features": [
    {
      "name": "Adaptive Learning Path",
      "description": "Visual branching paths based on student performance",
      "elements": [
        "Personalized recommendations with AI-driven UI"
      ]
    },
    {
      "name": "Community Engagement Hub",
      "description": "Student interaction and showcase platform",
      "elements": [
        "Student portfolios and showcases",
        "Collaborative project spaces",
        "Peer review interfaces"
      ]
    },
    {
      "name": "Virtual Study Environments",
      "description": "Focus-enhancing features",
      "elements": [
        "Pomodoro timer with break reminders",
        "Ambient sound mixer",
        "Distraction-blocking mode"
      ]
    },
    {
      "name": "Integrated Note-Taking System",
      "description": "Built-in notes functionality",
      "elements": [
        "Split-screen view with course content",
        "Rich formatting options",
        "Searchable and categorizable",
        "Export functionality"
      ]
    }
  ]
}
```

## TECH_STACK
```json
{
  "frontend": {
    "framework": "React.js",
    "state_management": "Redux",
    "ui_library": "Material-UI",
    "styling": "Styled Components",
    "testing": "Jest + React Testing Library",
    "build_tool": "Webpack"
  },
  "backend": {
    "language": "Node.js",
    "framework": "Express.js",
    "api_architecture": "RESTful",
    "authentication": "JWT + OAuth2",
    "validation": "Joi"
  },
  "database": {
    "primary_db": "MySQL",
    "orm": "Sequelize",
    "caching": "Redis",
    "search_functionality": "MeiliSearch"
  },
  "database_alternatives": {
    "option1": {
      "primary_db": "MongoDB",
      "odm": "Mongoose",
      "benefits": ["No SQL knowledge required", "Flexible schema", "JSON-like document storage", "Easier learning curve"]
    },
    "option2": {
      "primary_db": "SQLite",
      "orm": "Sequelize",
      "benefits": ["File-based", "Zero configuration", "Good for smaller projects", "Low maintenance"]
    }
  },
  "infrastructure": {
    "hosting": "DigitalOcean",
    "cdn": "Cloudflare",
    "deployment": "Docker (basic container deployment)",
    "ci_cd": "GitHub Actions",
    "monitoring": "Datadog"
  },
  "infrastructure_alternatives": {
    "option1": {
      "hosting": "Heroku",
      "benefits": ["Zero infrastructure management", "Simple deployment via Git push", "Add-ons marketplace", "Free tier available"]
    },
    "option2": {
      "hosting": "Vercel + Supabase",
      "benefits": ["Frontend and backend as services", "Simple deployment", "Database GUI provided", "Auth system included"]
    },
    "option3": {
      "hosting": "Shared hosting with cPanel",
      "benefits": ["Most affordable", "Familiar GUI interface", "One-click installations", "Managed service"]
    }
  },
  "third_party_services": {
    "payment_processing": "Stripe",
    "email_service": "SendGrid",
    "video_conferencing": ["Zoom API", "Microsoft Teams API"],
    "file_storage": "AWS S3",
    "analytics": "Google Analytics"
  }
}
```
```

## DATABASE_SCHEMA
```json
{
  "tables": [
    {
      "name": "users",
      "description": "All system users including students, instructors, and administrators",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "email", "type": "VARCHAR(255)", "constraints": ["UNIQUE", "NOT NULL"]},
        {"name": "password_hash", "type": "VARCHAR(255)", "constraints": ["NOT NULL"]},
        {"name": "first_name", "type": "VARCHAR(100)", "constraints": ["NOT NULL"]},
        {"name": "last_name", "type": "VARCHAR(100)", "constraints": ["NOT NULL"]},
        {"name": "role", "type": "ENUM", "values": ["student", "instructor", "admin"], "constraints": ["NOT NULL"]},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "student_profiles",
      "description": "Extended information for student users",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "user_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "bio", "type": "TEXT"},
        {"name": "profile_picture", "type": "VARCHAR(255)"},
        {"name": "preferences", "type": "JSONB"},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "courses",
      "description": "Available courses in the system",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "title", "type": "VARCHAR(255)", "constraints": ["NOT NULL"]},
        {"name": "description", "type": "TEXT", "constraints": ["NOT NULL"]},
        {"name": "instructor_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "price", "type": "DECIMAL(10,2)"},
        {"name": "duration_weeks", "type": "INTEGER"},
        {"name": "level", "type": "ENUM", "values": ["beginner", "intermediate", "advanced"]},
        {"name": "is_published", "type": "BOOLEAN", "constraints": ["DEFAULT FALSE"]},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "modules",
      "description": "Course modules/sections",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "course_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "title", "type": "VARCHAR(255)", "constraints": ["NOT NULL"]},
        {"name": "description", "type": "TEXT"},
        {"name": "order_number", "type": "INTEGER", "constraints": ["NOT NULL"]},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "lessons",
      "description": "Individual lessons within modules",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "module_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "title", "type": "VARCHAR(255)", "constraints": ["NOT NULL"]},
        {"name": "content", "type": "TEXT"},
        {"name": "video_url", "type": "VARCHAR(255)"},
        {"name": "duration_minutes", "type": "INTEGER"},
        {"name": "order_number", "type": "INTEGER", "constraints": ["NOT NULL"]},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "enrollments",
      "description": "Student course enrollments",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "student_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "course_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "enrollment_date", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "status", "type": "ENUM", "values": ["active", "completed", "withdrawn", "suspended"]},
        {"name": "completion_percentage", "type": "DECIMAL(5,2)", "constraints": ["DEFAULT 0"]},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "assignments",
      "description": "Course assignments",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "lesson_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "title", "type": "VARCHAR(255)", "constraints": ["NOT NULL"]},
        {"name": "description", "type": "TEXT", "constraints": ["NOT NULL"]},
        {"name": "due_date", "type": "TIMESTAMP"},
        {"name": "points_possible", "type": "INTEGER"},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "submissions",
      "description": "Assignment submissions by students",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "assignment_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "student_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "submitted_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "content", "type": "TEXT"},
        {"name": "file_url", "type": "VARCHAR(255)"},
        {"name": "grade", "type": "DECIMAL(5,2)"},
        {"name": "feedback", "type": "TEXT"},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "progress_tracking",
      "description": "Tracks student progress through course materials",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "student_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "lesson_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "status", "type": "ENUM", "values": ["not_started", "in_progress", "completed"]},
        {"name": "last_accessed_at", "type": "TIMESTAMP"},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "discussions",
      "description": "Forum discussions for courses",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "course_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "title", "type": "VARCHAR(255)", "constraints": ["NOT NULL"]},
        {"name": "created_by", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    },
    {
      "name": "discussion_posts",
      "description": "Individual posts within discussions",
      "fields": [
        {"name": "id", "type": "UUID", "constraints": ["PRIMARY KEY"]},
        {"name": "discussion_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "user_id", "type": "UUID", "constraints": ["FOREIGN KEY", "NOT NULL"]},
        {"name": "content", "type": "TEXT", "constraints": ["NOT NULL"]},
        {"name": "parent_post_id", "type": "UUID", "constraints": ["FOREIGN KEY"]},
        {"name": "created_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]},
        {"name": "updated_at", "type": "TIMESTAMP", "constraints": ["NOT NULL"]}
      ]
    }
  ],
  "indexes": [
    {"table": "users", "fields": ["email"], "type": "BTREE"},
    {"table": "courses", "fields": ["instructor_id"], "type": "BTREE"},
    {"table": "modules", "fields": ["course_id", "order_number"], "type": "BTREE"},
    {"table": "lessons", "fields": ["module_id", "order_number"], "type": "BTREE"},
    {"table": "enrollments", "fields": ["student_id", "course_id"], "type": "BTREE"},
    {"table": "progress_tracking", "fields": ["student_id", "lesson_id"], "type": "BTREE"}
  ],
  "relationships": [
    {"from": "student_profiles", "to": "users", "type": "one_to_one", "fields": ["user_id", "id"]},
    {"from": "courses", "to": "users", "type": "many_to_one", "fields": ["instructor_id", "id"]},
    {"from": "modules", "to": "courses", "type": "many_to_one", "fields": ["course_id", "id"]},
    {"from": "lessons", "to": "modules", "type": "many_to_one", "fields": ["module_id", "id"]},
    {"from": "enrollments", "to": "users", "type": "many_to_one", "fields": ["student_id", "id"]},
    {"from": "enrollments", "to": "courses", "type": "many_to_one", "fields": ["course_id", "id"]},
    {"from": "assignments", "to": "lessons", "type": "many_to_one", "fields": ["lesson_id", "id"]},
    {"from": "submissions", "to": "assignments", "type": "many_to_one", "fields": ["assignment_id", "id"]},
    {"from": "submissions", "to": "users", "type": "many_to_one", "fields": ["student_id", "id"]},
    {"from": "progress_tracking", "to": "users", "type": "many_to_one", "fields": ["student_id", "id"]},
    {"from": "progress_tracking", "to": "lessons", "type": "many_to_one", "fields": ["lesson_id", "id"]},
    {"from": "discussions", "to": "courses", "type": "many_to_one", "fields": ["course_id", "id"]},
    {"from": "discussions", "to": "users", "type": "many_to_one", "fields": ["created_by", "id"]},
    {"from": "discussion_posts", "to": "discussions", "type": "many_to_one", "fields": ["discussion_id", "id"]},
    {"from": "discussion_posts", "to": "users", "type": "many_to_one", "fields": ["user_id", "id"]},
    {"from": "discussion_posts", "to": "discussion_posts", "type": "many_to_one", "fields": ["parent_post_id", "id"]}
  ]
}
```

## COMPONENTS
```json
{
  "public_website": {
    "pages": [
      {
        "name": "homepage",
        "sections": ["hero", "featured_courses", "testimonials", "about", "call_to_action"],
        "data_dependencies": ["courses", "testimonials"]
      },
      {
        "name": "course_catalog",
        "features": ["filtering", "searching", "sorting", "pagination"],
        "data_dependencies": ["courses", "categories"]
      },
      {
        "name": "course_detail",
        "sections": ["overview", "syllabus", "instructor_bio", "pricing", "enrollment_button"],
        "data_dependencies": ["courses", "modules", "users"]
      },
      {
        "name": "registration",
        "sections": ["account_creation_form", "terms_conditions"],
        "data_dependencies": ["users"]
      },
      {
        "name": "about",
        "sections": ["mission_statement", "team_members", "company_history"],
        "data_dependencies": ["users"]
      },
      {
        "name": "contact",
        "sections": ["contact_form", "faq", "support_information"],
        "data_dependencies": []
      },
      {
        "name": "blog",
        "features": ["article_listing", "filtering", "search", "categories"],
        "data_dependencies": ["blog_posts", "categories"]
      }
    ]
  },
  "vle_platform": {
    "pages": [
      {
        "name": "login",
        "features": ["authentication_form", "password_reset", "remember_me"],
        "data_dependencies": ["users"]
      },
      {
        "name": "student_dashboard",
        "sections": ["enrolled_courses", "progress_summary", "notifications", "upcoming_deadlines"],
        "data_dependencies": ["enrollments", "courses", "progress_tracking", "assignments"]
      },
      {
        "name": "student_profile",
        "sections": ["personal_details", "learning_history", "achievements", "preferences"],
        "data_dependencies": ["users", "student_profiles", "enrollments"]
      },
      {
        "name": "course_learning",
        "sections": ["content_viewer", "navigation", "progress_tracker"],
        "data_dependencies": ["courses", "modules", "lessons", "progress_tracking"]
      },
      {
        "name": "assignment_submission",
        "features": ["file_upload", "text_editor", "submission_history"],
        "data_dependencies": ["assignments", "submissions"]
      },
      {
        "name": "discussion_forums",
        "features": ["thread_listing", "post_creation", "replies", "search"],
        "data_dependencies": ["discussions", "discussion_posts"]
      },
      {
        "name": "messaging",
        "features": ["conversation_list", "message_thread", "new_message"],
        "data_dependencies": ["messages", "users"]
      },
      {
        "name": "calendar",
        "features": ["month_view", "week_view", "event_creation", "reminders"],
        "data_dependencies": ["assignments", "courses", "custom_events"]
      }
    ]
  },
  "admin_panel": {
    "pages": [
      {
        "name": "dashboard",
        "sections": ["enrollment_stats", "user_stats", "revenue_overview", "system_health"],
        "data_dependencies": ["users", "enrollments", "payments", "system_logs"]
      },
      {
        "name": "user_management",
        "features": ["user_listing", "user_creation", "role_assignment", "account_status"],
        "data_dependencies": ["users", "roles", "permissions"]
      },
      {
        "name": "course_management",
        "features": ["course_listing", "course_creation", "content_upload", "publishing"],
        "data_dependencies": ["courses", "modules", "lessons"]
      },
      {
        "name": "enrollment_management",
        "features": ["enrollment_listing", "manual_enrollment", "bulk_operations"],
        "data_dependencies": ["enrollments", "users", "courses"]
      },
      {
        "name": "content_management",
        "features": ["media_library", "page_editor", "blog_management"],
        "data_dependencies": ["media_files", "pages", "blog_posts"]
      },
      {
        "name": "reports",
        "features": ["student_progress", "assessment_results", "revenue_reports"],
        "data_dependencies": ["enrollments", "progress_tracking", "submissions", "payments"]
      },
      {
        "name": "settings",
        "sections": ["site_configuration", "payment_settings", "email_templates", "integrations"],
        "data_dependencies": ["system_settings", "payment_gateways", "email_templates"]
      }
    ]
  }
}
```

## API_ENDPOINTS
```json
{
  "authentication": [
    {"method": "POST", "path": "/api/auth/register", "description": "Create a new user account"},
    {"method": "POST", "path": "/api/auth/login", "description": "Authenticate a user and receive JWT"},
    {"method": "POST", "path": "/api/auth/refresh-token", "description": "Refresh authentication token"},
    {"method": "POST", "path": "/api/auth/forgot-password", "description": "Initiate password reset process"},
    {"method": "POST", "path": "/api/auth/reset-password", "description": "Complete password reset with token"}
  ],
  "courses": [
    {"method": "GET", "path": "/api/courses", "description": "List all published courses"},
    {"method": "GET", "path": "/api/courses/:id", "description": "Get detailed course information"},
    {"method": "POST", "path": "/api/courses", "description": "Create a new course (admin/instructor)"},
    {"method": "PUT", "path": "/api/courses/:id", "description": "Update course information (admin/instructor)"},
    {"method": "DELETE", "path": "/api/courses/:id", "description": "Delete a course (admin/instructor)"},
    {"method": "GET", "path": "/api/courses/:id/modules", "description": "List all modules for a course"},
    {"method": "GET", "path": "/api/courses/:id/students", "description": "List all enrolled students (admin/instructor)"}
  ],
  "modules": [
    {"method": "GET", "path": "/api/modules/:id", "description": "Get detailed module information"},
    {"method": "POST", "path": "/api/modules", "description": "Create a new module (admin/instructor)"},
    {"method": "PUT", "path": "/api/modules/:id", "description": "Update module information (admin/instructor)"},
    {"method": "DELETE", "path": "/api/modules/:id", "description": "Delete a module (admin/instructor)"},
    {"method": "GET", "path": "/api/modules/:id/lessons", "description": "List all lessons in a module"}
  ],
  "lessons": [
    {"method": "GET", "path": "/api/lessons/:id", "description": "Get detailed lesson information"},
    {"method": "POST", "path": "/api/lessons", "description": "Create a new lesson (admin/instructor)"},
    {"method": "PUT", "path": "/api/lessons/:id", "description": "Update lesson information (admin/instructor)"},
    {"method": "DELETE", "path": "/api/lessons/:id", "description": "Delete a lesson (admin/instructor)"},
    {"method": "GET", "path": "/api/lessons/:id/assignments", "description": "List all assignments for a lesson"}
  ],
  "enrollments": [
    {"method": "GET", "path": "/api/enrollments", "description": "List current user's enrollments"},
    {"method": "POST", "path": "/api/enrollments", "description": "Enroll in a course"},
    {"method": "GET", "path": "/api/enrollments/:id", "description": "Get enrollment details"},
    {"method": "PUT", "path": "/api/enrollments/:id/status", "description": "Update enrollment status (admin)"}
  ],
  "assignments": [
    {"method": "GET", "path": "/api/assignments/:id", "description": "Get assignment details"},
    {"method": "POST", "path": "/api/assignments", "description": "Create a new assignment (admin/instructor)"},
    {"method": "PUT", "path": "/api/assignments/:id", "description": "Update assignment (admin/instructor)"},
    {"method": "DELETE", "path": "/api/assignments/:id", "description": "Delete assignment (admin/instructor)"}
  ],
  "submissions": [
    {"method": "GET", "path": "/api/submissions/assignment/:id", "description": "Get user's submission for assignment"},
    {"method": "POST", "path": "/api/submissions", "description": "Submit assignment work"},
    {"method": "PUT", "path": "/api/submissions/:id", "description": "Update submission before deadline"},
    {"method": "GET", "path": "/api/submissions/:id/feedback", "description": "Get feedback for submission"}
  ],
  "progress": [
    {"method": "GET", "path": "/api/progress/course/:id", "description": "Get user's progress in course"},
    {"method": "POST", "path": "/api/progress", "description": "Update progress status for a lesson"},
    {"method": "GET", "path": "/api/progress/summary", "description": "Get overall progress summary for user"}
  ],
  "users": [
    {"method": "GET", "path": "/api/users/me", "description": "Get current user profile"},
    {"method": "PUT", "path": "/api/users/me", "description": "Update current user profile"},
    {"method": "GET", "path": "/api/users/:id", "description": "Get user by ID (admin)"},
    {"method": "PUT", "path": "/api/users/:id", "description": "Update user by ID (admin)"},
    {"method": "DELETE", "path": "/api/users/:id", "description": "Delete user (admin)"}
  ],
  "discussions": [
    {"method": "GET", "path": "/api/discussions/course/:id", "description": "Get discussions for course"},
    {"method": "POST", "path": "/api/discussions", "description": "Create new discussion thread"},
    {"method": "GET", "path": "/api/discussions/:id/posts", "description": "Get posts in discussion thread"},
    {"method": "POST", "path": "/api/discussions/:id/posts", "description": "Create new post in discussion"}
  ],
  "integrations": [
    {"method": "GET", "path": "/api/integrations/zoom/meetings", "description": "List Zoom meetings for user"},
    {"method": "POST", "path": "/api/integrations/zoom/meetings", "description": "Create Zoom meeting"},
    {"method": "GET", "path": "/api/integrations/teams/channels", "description": "List Teams channels for user"}
  ],
  "payments": [
    {"method": "POST", "path": "/api/payments/create-intent", "description": "Create payment intent"},
    {"method": "GET", "path": "/api/payments/history", "description": "Get payment history for user"},
    {"method": "POST", "path": "/api/payments/refund", "description": "Process refund (admin)"}
  ],
  "admin": [
    {"method": "GET", "path": "/api/admin/stats/overview", "description": "Get system overview statistics"},
    {"method": "GET", "path": "/api/admin/stats/courses", "description": "Get course statistics"},
    {"method": "GET", "path": "/api/admin/stats/users", "description": "Get user statistics"},
    {"method": "GET", "path": "/api/admin/stats/revenue", "description": "Get revenue statistics"}
  ]
}
```

## IMPLEMENTATION_PHASES
```json
[
  {
    "phase_number": 1,
    "name": "Requirements & Planning",
    "duration_weeks": 4,
    "deliverables": [
      "Detailed project requirements document",
      "Database schema design",
      "API endpoint specification",
      "User flow diagrams",
      "Project timeline and resource allocation"
    ]
  },
  {
    "phase_number": 2,
    "name": "Design & Prototyping",
    "duration_weeks": 4,
    "deliverables": [
      "UI/UX wireframes",
      "Design system",
      "Interactive prototypes",
      "User testing feedback",
      "Finalized design assets"
    ]
  },
  {
    "phase_number": 3,
    "name": "Public Website Development",
    "duration_weeks": 8,
    "deliverables": [
      "Homepage implementation",
      "Course catalog and detail pages",
      "Registration system",
      "About and contact pages",
      "Responsive design implementation"
    ]
  },
  {
    "phase_number": 4,
    "name": "VLE Platform Development",
    "duration_weeks": 12,
    "deliverables": [
      "Authentication system",
      "Student dashboard",
      "Course content delivery system",
      "Assignment submission system",
      "Progress tracking",
      "Discussion forums",
      "Messaging system"
    ]
  },
  {
    "phase_number": 5,
    "name": "Admin Panel Development",
    "duration_weeks": 6,
    "deliverables": [
      "Admin dashboard",
      "User management interface",
      "Course management tools",
      "Content management system",
      "Reporting features"
    ]
  },
  {
    "phase_number": 6,
    "name": "Integration",
    "duration_weeks": 4,
    "deliverables": [
      "Payment processing integration",
      "Email notification system",
      "Third-party teaching platform integrations",
      "Analytics implementation"
    ]
  },
  {
    "phase_number": 7,
    "name": "Testing & QA",
    "duration_weeks": 4,
    "deliverables": [
      "Unit testing",
      "Integration testing",
      "User acceptance testing",
      "Performance testing",
      "Security audit",
      "Bug fixes and improvements"
    ]
  },
  {
    "phase_number": 8,
    "name": "Deployment & Launch",
    "duration_weeks": 2,
    "deliverables": [
      "Production environment setup",
      "Data migration",
      "Launch checklist completion",
      "Monitoring and alerting setup",
      "Initial user onboarding"
    ]
  }
]
```

## USER_ROLES_AND_PERMISSIONS
```json
{
  "roles": [
    {
      "name": "student",
      "description": "Regular learner with access to enrolled courses",
      "base_permissions": [
        "view_public_pages",
        "enroll_in_courses",
        "view_enrolled_course_content",
        "submit_assignments",
        "participate_in_discussions",
        "message_instructors",
        "view_own_profile",
        "edit_own_profile"
      ]
    },
    {
      "name": "instructor",
      "description": "Course creator and teacher",
      "base_permissions": [
        "view_public_pages",
        "create_courses",
        "edit_own_courses",
        "manage_course_content",
        "grade_assignments",
        "message_students",
        "view_course_analytics",
        "create_discussions",
        "moderate_course_discussions",
        "view_own_profile",
        "edit_own_profile"
      ]
    },
    {
      "name": "admin",
      "description": "Platform administrator with full access",
      "base_permissions": [
        "all_student_permissions",
        "all_instructor_permissions",
        "manage_all_courses",
        "manage_all_users",
        "view_site_analytics",
        "configure_system_settings",
        "manage_payment_settings",
        "manage_integrations",
        "view_financial_reports"
      ]
    }
  ],
  "permission_details": {
    "content_access": {
      "view_public_pages": "Access to homepage, course catalog, blog, etc.",
      "view_enrolled_course_content": "Access to lessons and materials for enrolled courses",
      "view_all_course_content": "Admin access to all course content"
    },
    "course_management": {
      "create_courses": "Ability to create new courses",
      "edit_own_courses": "Modify courses created by the user",
      "manage_all_courses": "Modify any course in the system",
      "publish_courses": "Make courses visible to students"
    },
    "user_management": {
      "view_own_profile": "See personal profile information",
      "edit_own_profile": "Update personal profile information",
      "view_all_profiles": "Access all user profiles",
      "create_users": "Add new users to the system",
      "edit_users": "Modify user information",
      "delete_users": "Remove users from the system",
      "assign_roles": "Change user permission levels"
    },
    "learning_activities": {
      "enroll_in_courses": "Join available courses",
      "submit_assignments": "Upload assignment submissions",
      "participate_in_discussions": "Post in discussion forums",
      "message_instructors": "Send private messages to course instructors",
      "message_students": "Send private messages to enrolled students"
    },
    "teaching_activities": {
      "manage_course_content": "Add, edit, organize course materials",
      "grade_assignments": "Review and evaluate student submissions",
      "create_discussions": "Start new discussion threads",
      "moderate_course_discussions": "Edit/remove inappropriate posts"
    },
    "administration": {
      "view_site_analytics": "Access platform usage statistics",
      "view_financial_reports": "See revenue and payment information",
      "configure_system_settings": "Modify global platform settings",
      "manage_payment_settings": "Configure payment providers and options",
      "manage_integrations": "Set up third-party service connections"
    }
  }
}
```

## SECURITY_REQUIREMENTS
```json
{
  "authentication": {
    "password_requirements": {
      "minimum_length": 8,
      "require_uppercase": true,
      "require_lowercase": true,
      "require_numbers": true,
      "require_special_characters": true
    },
    "session_management": {
      "token_expiration_hours": 24,
      "refresh_token_expiration_days": 7,
      "max_failed_login_attempts": 5,
      "lockout_duration_minutes": 30
    },
    "two_factor_authentication": {
      "available_methods": ["SMS", "email", "authenticator_app"],
      "required_for_roles": ["admin"]
    }
  },
  "data_protection": {
    "encryption": {
      "in_transit": "TLS 1.3",
      "at_rest": "AES-256",
      "sensitive_fields": ["password_hash", "payment_information"]
    },
    "backup": {
      "frequency": "daily",
      "retention_period_days": 30,
      "encryption": true
    }
  },
  "compliance": {
    "gdpr": {
      "data_subject_rights_supported": true,
      "privacy_policy_required": true,
      "data_processing_agreements_required": true
    },
    "accessibility": {
      "wcag_level": "2.1 AA",
      "screen_reader_compatibility": true
    }
  },
  "penetration_testing": {
    "frequency": "bi-annual",
    "scope": ["application", "infrastructure", "api"]
  },
  "vulnerability_management": {
    "dependency_scanning": true,
    "security_patches_sla_days": 7,
    "critical_vulnerabilities_sla_hours": 24,
    "automated_scanning_frequency": "daily"
  }