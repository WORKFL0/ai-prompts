# MSP Incident Response Generator

## Category
Business

## Context
MSP teams need to respond quickly and professionally to customer incidents. This prompt helps generate structured incident responses, including initial acknowledgment, status updates, and resolution communications for various types of IT issues.

## Goal
Create professional, clear, and reassuring incident response communications that maintain customer confidence while providing necessary technical information and next steps.

## Prompt Template

```
You are an experienced MSP (Managed Service Provider) incident response specialist. I need help crafting professional incident response communications.

**Incident Details:**
- Customer: [Company name]
- Issue Type: [Server outage/Network connectivity/Email issues/Security incident/Software malfunction/Other]
- Severity: [Critical/High/Medium/Low]
- Affected Systems: [List of affected systems/services]
- Business Impact: [Description of how this affects the customer's business]
- Current Status: [Investigation started/Root cause identified/Temporary fix applied/Permanent fix in progress/Resolved]
- Timeline: [When issue started, ETA for resolution]

Please provide:

1. **Initial Response Email**: Professional acknowledgment of the incident
2. **Status Update Template**: For ongoing communication during resolution
3. **Resolution Communication**: Final update when issue is resolved
4. **Technical Summary**: Brief technical explanation for stakeholders
5. **Follow-up Actions**: Preventive measures and recommendations
6. **Internal Notes**: Key points for team documentation

Make communications customer-focused, professional, and reassuring while being transparent about the situation and resolution timeline.
```

## Example Usage

**Input:**
- Customer: MidSize Manufacturing BV
- Issue Type: Server outage
- Severity: Critical
- Affected Systems: Primary file server, ERP system
- Business Impact: Production planning and file access completely down
- Current Status: Root cause identified - failed disk in RAID array
- Timeline: Started 09:30, ETA for resolution: 14:00

**Output:**

### Initial Response Email
**Subject**: [URGENT] Server Outage - MidSize Manufacturing - Incident #MSM-2025-0531-001

Beste klant,

We hebben kennis genomen van de server uitval die uw primaire bestandsserver en ERP-systeem beïnvloedt. Dit incident heeft prioriteit KRITIEK gekregen en ons technisch team werkt er met onmiddellijke ingang aan.

**Incident Details:**
- Incident nummer: #MSM-2025-0531-001
- Gemeld om: 09:30
- Betroffenen systemen: Primaire bestandsserver, ERP-systeem
- Impact: Productie planning en bestandstoegang niet beschikbaar

**Onze aanpak:**
- Technisch team ter plaatse
- Diagnose in uitvoering
- Verwachte eerste update: binnen 30 minuten

We houden u op de hoogte van alle ontwikkelingen en werken aan een snelle oplossing.

Met vriendelijke groet,
Workflo Support Team

### Status Update Template
**Subject**: [UPDATE] Server Outage - MidSize Manufacturing - Incident #MSM-2025-0531-001

Beste klant,

**Status update om 11:15:**

✅ **Root cause geïdentificeerd**: Defecte schijf in RAID-array
✅ **Oplossing bepaald**: RAID-array rebuild met vervangende schijf
🔄 **Huidige actie**: Hardware vervanging in uitvoering

**Timeline update:**
- Verwachte oplossing: 14:00
- Systemen geleidelijk online vanaf 13:30
- Volledige functionaliteit: 14:00

Uw data is veilig door onze RAID-configuratie. We verwachten geen dataverlies.

Volgende update: 12:30 of bij significante ontwikkelingen.

### Resolution Communication
**Subject**: [RESOLVED] Server Outage - MidSize Manufacturing - Incident #MSM-2025-0531-001

Beste klant,

Goed nieuws! Het server incident is succesvol opgelost.

**Oplossing voltooid om**: 13:45
**Alle systemen operationeel**: Bevestigd om 14:00
**Dataverlies**: Geen
**Totale downtime**: 4 uur en 15 minuten

**Uitgevoerde werkzaamheden:**
- Defecte schijf vervangen
- RAID-array volledig gerebuild
- Systeem functionaliteit geverifieerd
- Performance tests uitgevoerd

**Preventieve maatregelen:**
- Extra monitoring toegevoegd aan RAID-status
- Preventieve vervanging van aging disks ingepland
- Backup verificatie uitgevoerd

We excuseren ons voor het ongemak. Een gedetailleerd incident rapport volgt binnen 24 uur.

Met vriendelijke groet,
Florian de Haan - CEO Workflo

## Testing Status
✅ **Tested** - Used in real MSP environments with positive customer feedback on clarity and professionalism.

## Tags
- MSP
- Incident Response
- Customer Communication
- IT Support
- Business Continuity
- Technical Support

## Version
1.0

## Last Updated
Mei 2025
