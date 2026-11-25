# VenueTern — proposed AWS architecture

VenueTern uses AWS to learn from every event your venue has hosted and serve forecasts and plans to your team — securely, per venue.

## Request flow

1. Bookings
2. Amazon S3
3. AWS Lambda
4. SageMaker AI
5. DynamoDB
6. Ops manager
7. Bedrock briefing

## Services

### Amazon SageMaker AI

**Role:** Forecast attendance and arrivals

Trains models on booking histories, event types, seasonality and actual turnout to forecast attendance ranges and 15-minute arrival curves.

### Amazon Bedrock

**Role:** Draft team briefings

Turns an approved event plan into a clear briefing for the stand-up — staffing, rooms, peak times — for the manager to edit and share.

### Amazon S3

**Role:** Store booking histories

Keeps booking exports and post-event records encrypted and versioned as the training history for each venue.

### Amazon DynamoDB

**Role:** Serve plans and forecasts

Holds events, forecasts, recommendations and approvals for fast access from the events workspace.

### AWS Lambda

**Role:** Import and recalculate

Processes booking imports, links them to events and recalculates recommendations whenever bookings change.

## Principles

- **Per-venue models** — Every venue’s crowd is different, so every venue gets its own model.
- **Ranges, not promises** — Forecasts show a likely range, not a single number.
- **Guest privacy** — Plans use counts, not personal guest data.

## Safeguards

- **Managers approve plans** — Recommendations are a starting point; your operations manager decides.
- **Safety limits respected** — Recommendations never exceed the room capacity limits you set. Crowd safety stays with your safety officers.
- **Explained forecasts** — Each forecast shows the past events it learned from.
- **No guest profiling** — Forecasts use aggregate booking counts, not individual guest data.

## MVP scope

We import 12–24 months of your bookings and event outcomes, forecast attendance for upcoming events, and recommend staffing and room allocation your team reviews before each event.

- Booking history import
- Attendance and arrival forecasts
- Staffing estimates by role
- Room allocation suggestions
- Post-event accuracy report
