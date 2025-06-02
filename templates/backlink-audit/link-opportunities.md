# Link Opportunities Excel Template Structure

## Overview
This document outlines the structure for the link-opportunities.xlsx file, designed to help SEO professionals identify, track, and manage link building opportunities.

## Sheet Structure

### Sheet 1: Opportunity Dashboard
**Key Metrics Overview:**
- Total Opportunities Identified
- Success Rate by Campaign Type
- Average Domain Rating of Prospects
- Outreach Response Rate
- Links Acquired This Month
- Pipeline Value (estimated traffic potential)

**Campaign Performance Charts:**
- Success rate by link type
- DR distribution of acquired links
- Monthly link acquisition trend
- Response rate by outreach template

### Sheet 2: Prospect Database
| Column | Description | Example |
|--------|-------------|---------|
| Prospect ID | Unique identifier | LINK-001 |
| Target Domain | Prospect website | example-blog.com |
| Target URL | Specific page for link | example-blog.com/resources |
| Domain Rating | Authority score (0-100) | 65 |
| Organic Traffic | Monthly organic visitors | 15,000 |
| Industry/Niche | Business category | Digital Marketing |
| Country | Geographic location | United States |
| Language | Content language | English |
| Contact Name | Decision maker | John Smith |
| Email Address | Outreach contact | john@example-blog.com |
| Job Title | Contact's position | Content Manager |
| Social Profiles | LinkedIn/Twitter | linkedin.com/in/johnsmith |
| Link Type | Opportunity category | Guest Post |
| Content Topic | Suggested topic | SEO Best Practices |
| Relevance Score | Topical alignment (1-10) | 9 |
| Difficulty Score | Acquisition difficulty (1-10) | 6 |
| Estimated Value | Traffic potential | High |
| Competitor Links | Do competitors have links? | Yes |
| Last Updated | Record update date | 2024-01-15 |
| Source | How prospect was found | Competitor analysis |
| Notes | Additional context | Accepts guest posts |

### Sheet 3: Outreach Tracking
| Column | Description |
|--------|-------------|
| Prospect ID | Links to prospect database |
| Campaign Name | Outreach campaign |
| Email Template | Template used |
| First Contact Date | Initial outreach |
| Follow-up 1 Date | First follow-up |
| Follow-up 2 Date | Second follow-up |
| Follow-up 3 Date | Final follow-up |
| Response Date | When they replied |
| Response Type | Positive/Negative/Neutral |
| Status | Not contacted/Sent/Response/Accepted/Rejected |
| Success Reason | Why it worked |
| Rejection Reason | Why it failed |
| Link Acquired Date | When link went live |
| Final Link URL | Actual link location |
| Anchor Text Used | Final anchor text |
| Next Action | Required follow-up |
| Relationship Level | Cold/Warm/Hot |

### Sheet 4: Content Calendar
| Column | Description |
|--------|-------------|
| Content ID | Unique identifier |
| Title | Content piece title |
| Target Keyword | Primary keyword |
| Content Type | Blog post/Infographic/Guide |
| Target Prospects | Number of prospects |
| Creation Status | Not started/In progress/Complete |
| Writer Assigned | Content creator |
| Due Date | Deadline |
| Publish Date | Go-live date |
| Performance Metrics | Views/Shares/Links |
| Promotion Strategy | Distribution plan |

### Sheet 5: Competitor Analysis
| Column | Description |
|--------|-------------|
| Competitor | Competitor domain |
| Their Link Source | Where they got links |
| Link URL | Specific link location |
| Anchor Text | Their anchor text |
| Link Type | Editorial/Guest/Directory |
| Domain Rating | Source authority |
| Traffic Estimate | Source traffic |
| Acquisition Difficulty | How hard to replicate |
| Our Status | Pursued/Acquired/Rejected |
| Gap Opportunity | Unique to competitor |
| Priority Level | High/Medium/Low |

### Sheet 6: Resource Page Opportunities
| Column | Description |
|--------|-------------|
| Resource Page URL | Target resource page |
| Page Title | Resource page title |
| Domain Rating | Page authority |
| Last Updated | When page was updated |
| Resource Categories | Types of resources listed |
| Our Fit | How well we fit |
| Contact Method | How to request inclusion |
| Submission Guidelines | Requirements |
| Submission Date | When we applied |
| Status | Pending/Approved/Rejected |
| Link Added Date | When link appeared |

### Sheet 7: Campaign Performance
| Column | Description |
|--------|-------------|
| Campaign Name | Campaign identifier |
| Campaign Type | Guest post/Resource/Directory |
| Start Date | Campaign launch |
| End Date | Campaign completion |
| Prospects Contacted | Total outreach |
| Response Rate | Reply percentage |
| Acceptance Rate | Success percentage |
| Links Acquired | Total links gained |
| Traffic Generated | Referral traffic |
| Keyword Rankings | Ranking improvements |
| ROI | Return on investment |
| Lessons Learned | Key takeaways |

## Formulas and Calculations

### Success Rate Calculation:
```excel
=COUNTIFS(Status,"Accepted")/COUNTIFS(Status,"<>"&"Not contacted")*100
```

### Average Domain Rating:
```excel
=AVERAGE(DomainRating[ProspectsContacted])
```

### Response Rate:
```excel
=COUNTIFS(ResponseType,"<>"&"")/COUNTIFS(Status,"Sent")*100
```

### Pipeline Value Score:
```excel
=SUMPRODUCT(OrganicTraffic*RelevanceScore*10)/1000
```

## Conditional Formatting Rules

### Domain Rating:
- Green (60+): High authority
- Yellow (30-59): Medium authority  
- Red (<30): Low authority

### Difficulty Score:
- Green (1-3): Easy
- Yellow (4-6): Moderate
- Red (7-10): Difficult

### Status Tracking:
- Green: Accepted/Link Acquired
- Yellow: In Progress/Pending
- Red: Rejected/No Response

## Data Integration Sources

### Prospect Research Tools:
- Ahrefs Content Explorer
- BuzzSumo
- Hunter.io for email finding
- LinkedIn Sales Navigator
- HARO (Help a Reporter Out)

### Competitor Analysis:
- Ahrefs Site Explorer
- SEMrush Backlink Gap
- Majestic Site Explorer

### Email Outreach:
- Mailshake
- Pitchbox
- BuzzStream
- GMass

## Automation Opportunities

### Data Import:
- CSV import from prospecting tools
- API connections where available
- Regular data refreshes

### Email Tracking:
- Open/click tracking integration
- Response categorization
- Follow-up scheduling

### Performance Monitoring:
- Link status checking
- Traffic monitoring
- Ranking impact tracking

## Best Practices

### Prospect Qualification:
1. Minimum DR threshold (usually 20+)
2. Topical relevance score 6+
3. Recent content activity
4. Clear contact information
5. Evidence of linking to others

### Outreach Strategy:
1. Personalized subject lines
2. Value-first approach
3. Clear call-to-action
4. Professional email signature
5. Systematic follow-up schedule

### Relationship Building:
1. Social media engagement
2. Content sharing and commenting
3. Mutual value creation
4. Long-term partnership focus
5. Regular relationship maintenance

## Reporting Templates

### Weekly Report:
- New prospects added
- Outreach sent/responses received
- Links acquired
- Campaign performance updates

### Monthly Report:
- Overall campaign metrics
- ROI analysis
- Strategy adjustments needed
- Competitive landscape changes

This template provides a comprehensive framework for managing link building campaigns from prospect identification through link acquisition and performance measurement.
