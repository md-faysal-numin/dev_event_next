# PostHog post-wizard report

The wizard has completed a deep integration of your DevEvent Next.js project. PostHog has been configured using the modern `instrumentation-client.ts` approach (recommended for Next.js 15.3+), with a reverse proxy setup for improved tracking reliability and reduced ad-blocker interference.

## Integration Summary

The following files were created or modified:

| File | Change |
|------|--------|
| `.env` | Created with `NEXT_PUBLIC_POSTHOG_KEY` and `NEXT_PUBLIC_POSTHOG_HOST` environment variables |
| `instrumentation-client.ts` | Created to initialize PostHog on client-side with error tracking enabled |
| `next.config.ts` | Updated with reverse proxy rewrites for EU PostHog region |
| `components/ExploreBtn.tsx` | Added PostHog event tracking for CTA button clicks |
| `components/EventCard.tsx` | Added PostHog event tracking for event card clicks with event metadata |
| `components/Navbar.tsx` | Added PostHog event tracking for all navigation interactions |

## Events Instrumented

| Event Name | Description | File |
|------------|-------------|------|
| `explore_events_clicked` | User clicked the 'Explore Events' button on the homepage - key CTA for engaging with content | `components/ExploreBtn.tsx` |
| `event_card_clicked` | User clicked on an event card to view event details - tracks interest in specific events (includes event title, slug, location, date, time) | `components/EventCard.tsx` |
| `nav_home_clicked` | User clicked on 'Home' link in navigation | `components/Navbar.tsx` |
| `nav_events_clicked` | User clicked on 'Events' link in navigation - shows intent to browse events | `components/Navbar.tsx` |
| `nav_create_event_clicked` | User clicked on 'Create Event' link - high-value action indicating intent to contribute | `components/Navbar.tsx` |
| `logo_clicked` | User clicked on the DevEvent logo to navigate home | `components/Navbar.tsx` |

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

### Dashboard
- [Analytics basics](https://eu.posthog.com/project/113975/dashboard/480137) - Core analytics dashboard tracking user engagement and conversion events

### Insights
- [Event Card Clicks by Event](https://eu.posthog.com/project/113975/insights/m4pmXrFN) - Tracks which events are getting the most attention from users
- [Navigation Flow](https://eu.posthog.com/project/113975/insights/Xomp0c4e) - Tracks user navigation patterns through the app header
- [Explore to Event Funnel](https://eu.posthog.com/project/113975/insights/YFf66G9A) - Conversion funnel from clicking Explore Events to viewing an event
- [Event Interest by Location](https://eu.posthog.com/project/113975/insights/ZrYqJXBq) - Shows event clicks broken down by event location to understand geographic interest
- [Create Event Intent](https://eu.posthog.com/project/113975/insights/P6Jf01a7) - Tracks users showing high intent to create events - a key conversion indicator

## Configuration Details

- **PostHog Host**: EU region (`https://eu.i.posthog.com`)
- **Reverse Proxy**: Enabled via Next.js rewrites at `/ingest/*`
- **Error Tracking**: Enabled (`capture_exceptions: true`)
- **Debug Mode**: Enabled in development environment
