---
name: cli-ui-design
description: CLI interface design specialist. Use PROACTIVELY to create terminal-inspired user interfaces with modern web technologies. Expert in CLI aesthetics, terminal themes, and command-line UX patterns.
enforcement_level: MEDIUM
violation_consequence: CLI interfaces may not feel authentic, may be inconsistent, or may have poor UX
---

# CLI UI Design

This skill provides comprehensive guidance for creating terminal-inspired web interfaces using modern web technologies. It emphasizes authentic terminal aesthetics and modern usability.

## Overview

CLI UI design involves creating terminal-inspired interfaces that feel authentic while providing modern web usability. This skill provides systematic approaches to CLI interface design.

## Core Expertise

### Terminal Aesthetics
- Monospace typography with fallback fonts: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace
- Terminal color schemes with CSS custom properties for consistent theming
- Command-line visual patterns like prompts, cursors, and status indicators
- ASCII art integration for headers and branding elements

### Design Principles

#### 1. Authentic Terminal Feel
- Core terminal styling patterns
- Terminal command sections
- Proper color schemes

#### 2. Command Line Elements
- Prompts: Use `$`, `>`, `⎿` symbols with accent colors
- Status Dots: Colored circles (green, orange, red) for system states
- Terminal Headers: ASCII art with proper spacing and alignment
- Command Structures: Clear hierarchy with prompts, commands, and parameters

#### 3. Color System
- Terminal background colors
- Terminal text colors
- Terminal borders
- Status colors (success, warning, error)

## Component Patterns

### Terminal Header
- ASCII art titles
- Status indicators
- Terminal subtitles

### Command Sections
- Command names with parameters
- Descriptions with terminal prompts
- Proper hierarchy

### Interactive Command Input
- Terminal prompts
- Search inputs
- Command-line examples

### Filter Chips
- Terminal-style filters
- Type indicators
- Active states

## Layout Structures

### Full Terminal Layout
- Terminal sections
- Grid systems
- Cards and containers

## Interactive Elements

### Buttons
- Terminal-style buttons
- Hover states
- Proper transitions

### Form Inputs
- Terminal inputs
- Focus states
- Proper styling

### Status Indicators
- Status dots
- Terminal dots
- Color coding

## Implementation Process

### Structure Analysis
1. Identify main sections and their terminal equivalents
2. Map interactive elements to command-line patterns
3. Plan ASCII art integration for headers and branding
4. Design command flow between sections

### CSS Architecture
1. CSS Custom Properties for terminal color scheme
2. Base Terminal Styles for main container
3. Component Patterns for command sections, inputs, buttons
4. Layout Utilities for grid and flex layouts
5. Responsive Design for mobile adaptations

### JavaScript Integration
- Minimal DOM manipulation for authentic feel
- Event handling with terminal-style feedback
- State management that reflects command-line workflows
- Keyboard shortcuts for power user experience

### Accessibility
- High contrast terminal color schemes
- Keyboard navigation support
- Screen reader compatibility with semantic HTML
- Focus indicators that match terminal aesthetics

## Quality Standards

### Visual Consistency
- All text uses monospace fonts
- Color scheme follows CSS custom properties
- Spacing follows 8px baseline grid
- Border radius consistent (4px for small, 8px for large)

### Terminal Authenticity
- Command prompts use proper symbols ($, >, ⎿)
- Status indicators use appropriate colors
- ASCII art is properly formatted
- Interactive feedback mimics terminal behavior

### Responsive Design
- Mobile-first approach maintained
- Terminal aesthetics preserved across devices
- Touch-friendly interactive elements
- Readable font sizes on all screens

### Performance
- CSS optimized for fast rendering
- Minimal JavaScript overhead
- Efficient use of CSS custom properties
- Proper asset loading strategies

## Best Practices

Focus on creating interfaces that feel authentically terminal-based while providing modern web usability. Every element should contribute to the command-line aesthetic while maintaining professional polish and user experience standards.
