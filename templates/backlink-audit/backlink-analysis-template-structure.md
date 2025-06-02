# Backlink Analysis Template Structure

## Overview
This document outlines the structure for the backlink-analysis-template.xlsx file. This template is designed to help SEO professionals analyze backlink profiles comprehensively.

## Sheet Structure

### Sheet 1: Summary Dashboard
- **Total Backlinks**: Count of all backlinks
- **Referring Domains**: Unique domains linking to the site
- **Domain Rating Distribution**: Breakdown by DR ranges (0-20, 21-40, 41-60, 61-80, 81-100)
- **Link Type Distribution**: Dofollow vs Nofollow percentages
- **Top Link Sources**: Most valuable referring domains
- **Risk Assessment**: Overall backlink profile health score

### Sheet 2: Raw Backlink Data
| Column | Description | Example |
|--------|-------------|---------|
| URL | Target page URL | https://example.com/page |
| Referring URL | Source page URL | https://referrer.com/article |
| Referring Domain | Root domain of the source | referrer.com |
| Anchor Text | Link anchor text | Click here |
| Link Type | Dofollow/Nofollow | Dofollow |
| Domain Rating | DR score (0-100) | 45 |
| Traffic | Monthly organic traffic | 1,250 |
| Link Position | Position in content | Body |
| Date Found | When link was discovered | 2024-01-15 |
| Link Status | Active/Broken/Redirect | Active |
| Relevance Score | Topical relevance (1-10) | 8 |
| Spam Score | Risk assessment (0-100) | 15 |

### Sheet 3: Domain Analysis
| Column | Description |
|--------|-------------|
| Referring Domain | Root domain |
| Domain Rating | Authority score |
| Organic Traffic | Monthly visitors |
| Backlinks to Domain | Total inbound links |
| Industry/Niche | Topical category |
| Language | Content language |
| Country | Geographic location |
| Link Count | Links from this domain |
| First Link Date | Oldest link found |
| Last Link Date | Most recent link |
| Link Growth Trend | Increasing/Stable/Declining |

### Sheet 4: Anchor Text Analysis
| Column | Description |
|--------|-------------|
| Anchor Text | Exact anchor text |
| Frequency | Number of occurrences |
| Percentage | % of total anchors |
| Category | Brand/Exact/Partial/Generic |
| Risk Level | Over-optimization risk |
| Recommendations | Suggested actions |

### Sheet 5: Competitor Comparison
| Column | Description |
|--------|-------------|
| Competitor | Competitor domain |
| Total Backlinks | Their backlink count |
| Referring Domains | Their referring domains |
| Average DR | Avg domain rating |
| Common Domains | Shared link sources |
| Gap Opportunities | Links they have we don't |
| Link Velocity | Monthly link growth |

### Sheet 6: Toxic Links Review
| Column | Description |
|--------|-------------|
| Referring URL | Suspicious link source |
| Referring Domain | Root domain |
| Risk Level | High/Medium/Low |
| Risk Factors | Specific issues found |
| Spam Score | Algorithmic risk score |
| Recommendation | Keep/Monitor/Disavow |
| Disavow Status | Submitted/Pending/Not needed |
| Notes | Manual review notes |

### Sheet 7: Link Building Opportunities
| Column | Description |
|--------|-------------|
| Target Domain | Prospective link source |
| Domain Rating | Authority score |
| Relevance Score | Topical alignment |
| Contact Email | Outreach contact |
| Link Type | Guest post/Resource/Directory |
| Outreach Status | Not contacted/Sent/Response |
| Success Probability | Estimated likelihood |
| Notes | Additional context |

## Formulas and Calculations

### Key Metrics Formulas:
- **Link Diversity Ratio**: =COUNTA(UniqueReferringDomains)/COUNTA(TotalBacklinks)
- **Authority Score**: =AVERAGE(DomainRatingColumn)
- **Risk Assessment**: =COUNTIF(RiskLevel,"High")/COUNTA(TotalLinks)*100
- **Anchor Text Diversity**: =COUNTA(UniqueAnchors)/COUNTA(TotalAnchors)

### Conditional Formatting Rules:
- Domain Rating: Green (80+), Yellow (40-79), Red (<40)
- Spam Score: Red (70+), Yellow (30-69), Green (<30)
- Link Status: Green (Active), Red (Broken)
- Risk Level: Red (High), Orange (Medium), Green (Low)

## Data Sources
Compatible with exports from:
- Ahrefs Site Explorer
- SEMrush Backlink Analytics
- Majestic Site Explorer
- Moz Link Explorer
- Google Search Console

## Usage Instructions
1. Export backlink data from your preferred SEO tool
2. Import raw data into "Raw Backlink Data" sheet
3. Use pivot tables and formulas to populate analysis sheets
4. Review toxic links and create disavow file if needed
5. Identify link building opportunities from competitor analysis
6. Generate executive summary with key findings and recommendations

## Maintenance
- Update monthly with fresh backlink data
- Monitor link status changes
- Track progress on disavow and outreach efforts
- Compare month-over-month growth metrics
