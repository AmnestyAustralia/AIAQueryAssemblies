# AIA Query Assemblies

Custom Blackbaud CRM query view assemblies developed for Amnesty International Australia (AIA). This solution extends the Blackbaud AppFx query framework with specialised query views for constituent data, revenue tracking, and rolling date calculations.

## Project Structure

The solution contains five BBCRM customisation assembly projects providing additional query views.

- **AIAConstituentQuery** - Constituent-related query views
- **AIARevenueQuery** - Recurring gift and revenue related query views
- **AIARollingDates** - Dynamic rolling date calculations
- **AIADateParts** - Date components (work in progress)
- **AIAUtilities** - Utility and helper query definitions

## Customisations

### AIAConstituentQuery

Custom query views for accessing constituent-related data from the Constituent node.

#### Constituent Appeal Mailing

- **Appeal Mailing (AIA)** - Queries constituent appeal mailing records. This is almost the same as the standard appeal mailing node but is significantly faster as it only checks appeal mailings (i.e. marketing efforts) and does not check email communication records.

#### Prospect Plans

- **Prospect Plan Participants (AIA)** - Queries prospect plans that a constituent is a non-primary participant for.

#### Address

- **Email Address (Primary) (AIA)** - Retrieves only primary email addresses for constituents. Otherwise identical to the standard email address node.

- **Phone (Primary) (AIA)** - Retrieves only primary phone numbers for constituents. Otherwise identical to the standard phone number node.

### AIARevenueQuery

Custom query views for recurring gift and revenue data from the Revenue node.

#### Recurring Gift Amendments

- **Recurring Gift Origin (AIA)** - Queries the original recurring gift details from the recurring gift amendment table's "Added" record.

- **Recurring Gift Amendments (AIA)** - Tracks the full history of recurring gifts from the recurring gift amendment table. Shows the type, date and details (old and new values) of each change with associated marketing information (appeal etc.).

#### Recurring Gift Installments

- **Recurring Gift Installments (AIA)** - Queries individual recurring gift installments. Includes installment amount, date, status (Expected, Past due, Paid, Skipped, Write-off), and past due date.

- **Recurring Gift Installment Payments (AIA)** - Queries payments applied to specific installments. Links payments back to their parent installments for reconciliation and tracking,

- **Recurring Gift Installment Events (AIA)** - Queries transaction events for installments including processing events, credit card authorisations, credit card rejections, direct debit rejections, and amount changes.

- **Recurring Gift Installment Writeoffs (AIA)** - Queries write-off transactions applied to installments.

### AIARollingDates

Provides dynamically calculated rolling date fields that can be joined to various record types for relative date filtering in queries. Adapted from a script by David Bourne (TWS).

Rolling date calculations include today, yesterday, tomorrow, period boundaries (first/last day of previous/current/next month, quarter, calendar year, fiscal year), backward rolling dates (2-31 days ago, 1-12 weeks ago, 1-18 months ago, 1-10 years ago), forward rolling dates (7-28 days ahead, 1-8 weeks ahead, 1-6 months ahead), and week-relative dates (this week, last week, next week day 1-7).

- **Constituent Rolling Dates (AIA)** - Rolling date fields Joined to the Constituent node.

- **Revenue Rolling Dates (AIA)** - Rolling date fields Joined to the Revenue node.

- **Interaction Rolling Dates (AIA)** - Rolling date calculations joined to the Interaction node.

- **Membership Rolling Dates (AIA)** - Rolling date calculations joined to the Membership node.

### AIADateParts

Query views for extracting date components from revenue records for analytics and reporting.

- **Revenue Date Parts (AIA)** - Extracts date components from revenue records including calendar year, month, quarter, week, day of year, day of month, and day of week. Also provides boolean flags for "This Month Any Year" and "This Day Any Year".

### AIAUtilities

Utility query views for system administration and query management.

- **Ad-hoc Query Columns (AIA)** - Queries the metadata of ad-hoc query definitions for usage of particular fields, tables and selections as filters or output columns. Shows column names, display names, usage (Select or Filter), query node information, filter operators and values. Useful for auditing and documenting existing ad-hoc queries in the system.
