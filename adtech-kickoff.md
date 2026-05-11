# AdTech Kick-off Meeting Prep

## Meeting Attendees
- Rob Nelson (VP Engineering)
- Abhishek Chatterjee (Solutions Architect)
- Steve Rayko (SVP Engineering)
- Nicklas Chapman

## Questions

### Segmentation Logic
- Is the user-to-segment relationship many-to-one or many-to-many?
- How does the system resolve conflicts when a user matches multiple segments?

### Data Pipeline
- What's the exact mechanism for computing segment membership? (Snowflake Tasks, external scheduler like Airflow/K8s CronJob, or Lytics-driven?)
- Is the Snowflake → Lytics sync batch (scheduled) or continuous? How frequently do segment memberships update?
- Is Lytics (vendor CDP) instead of, or as well as, a potential in-house CDP build? Have I misunderstood the CDP strategy?

### Personalize Edge
- What exactly does Personalize Edge do? Is it performing decisioning at the edge or just caching?
- How does Personalize Edge integrate with our existing Cloudfront CDN? Do we maintain Cloudfront for content delivery?

### Ad Platform Architecture (Custom Build)
- How does creative selection work within a line item? Are multiple creatives alternatives for A/B testing, or for serving different ad slot formats?

## Follow-up Actions
- Talk to Ossie and Stefan about Segmented Storefront frontend implementation
- Talk to Platform/Data team about segmentation logic and backend architecture
