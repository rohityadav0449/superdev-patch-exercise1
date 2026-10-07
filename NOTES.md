# Assignment Notes

## Fixes Implemented

### 1. Loading state not cleared on API failure
The frontend loading state remained active when the API request failed because setLoading(false) was missing from the catch block. I added it so errors are displayed correctly instead of keeping the UI in a loading state.

### 2. Removed unnecessary API delay
The backend controller contained an artificial Thread.sleep() based on the search query length. This caused unnecessary response delays. I removed the artificial delay so task searches respond immediately.

### 3. Improved pagination and status validation
The API now validates page and pageSize values and applies safe defaults for invalid values. Invalid task status values are handled with a clear HTTP 400 response instead of an unhandled exception.

### 4. Fixed task search SQL logic
The repository query had an AND/OR precedence issue. Because of this, archived tasks could appear when the description matched the search term. I added parentheses so archived tasks are always excluded and the optional status filter is applied consistently.

## Assumption

The application uses the existing H2 in-memory database and existing API structure. No database schema changes were required.
