# Supabase Web Client

A lightweight, browser-based client for interacting with Supabase databases through REST API. This tool provides a user-friendly interface to perform database operations, authentication, and API exploration without writing code.

## 🚀 Features

### 📊 Database Operations

- **Select Data**: Query tables with filtering, ordering, and pagination
- **Insert Data**: Add new records to tables with JSON input
- **Update Data**: Modify existing records with filters
- **Delete Data**: Remove records with safety confirmations

### 🔍 API Explorer

- **OpenAPI Specification**: Fetch and view complete API documentation
- **Table Discovery**: Automatically discover all tables and their schemas
- **RPC Functions**: List and execute stored procedures/functions

### 🔐 Authentication

- **User Sign Up**: Register new users with email/password
- **User Sign In**: Authenticate and obtain access tokens
- **User Info**: Retrieve current user information
- **Token Management**: Automatically handle access tokens

### ⚡ Advanced Features

- **Custom Tokens**: Support for custom access tokens
- **RPC Function Calls**: Execute PostgreSQL functions with parameters
- **Collapsible JSON Viewer**: Clean, organized response display
- **Local Storage**: Persistent configuration across sessions

## 📋 Prerequisites

- A Supabase project (create one at [supabase.com](https://supabase.com))
- Your Supabase project URL
- Your Supabase anon/public API key
- A modern web browser

## 🛠️ Installation

1. **Download the file**:

   ```bash
   git clone <repository-url>
   cd supabase-web-client
   ```

2. **Open in browser**:
   - Simply open `index.html` in your web browser
   - No build process or dependencies required
   - Works completely client-side

## ⚙️ Configuration

1. **Get Your Supabase Credentials**:

   - Go to your Supabase project dashboard
   - Navigate to Settings → API
   - Copy your Project URL and anon/public key

2. **Configure the Client**:

   - Open the application in your browser
   - Navigate to the "Configuration" tab (automatically shown on first load)
   - Enter your Supabase URL (e.g., `https://your-project.supabase.co`)
   - Enter your Supabase anon key
   - Optionally enter an access token (for authenticated requests)
   - Click "Save Configuration"

3. **Configuration Storage**:
   - Settings are stored in browser's localStorage
   - Credentials persist across browser sessions
   - Use "Clear Token" to remove stored access token

## 📖 Usage Guide

### 🔍 API Explorer

**Fetch OpenAPI Specification**:

- View your complete API schema
- Discover available endpoints
- Understand request/response formats

**List Tables**:

- Automatically discover all tables in your database
- View column names for each table
- Quick reference for database structure

**List RPC Functions**:

- Discover all stored procedures
- View function parameters
- Quick-launch functions directly from the list

### 📊 Select Data

Query your database tables:

1. **Table Name**: Enter the table name (e.g., `users`, `posts`)
2. **Select Columns**: Specify columns (use `*` for all)
   - Example: `id, name, email`
3. **Filter**: Apply PostgREST filters (optional)
   - Example: `id=eq.1` (equals)
   - Example: `age=gt.18` (greater than)
   - Example: `name=like.*John*` (pattern match)
4. **Order By**: Sort results (optional)
   - Example: `created_at.desc`
   - Example: `name.asc`
5. **Limit**: Number of records to return

### ➕ Insert Data

Add new records to tables:

1. **Table Name**: Target table
2. **JSON Data**: Enter JSON object or array
   ```json
   {
     "name": "John Doe",
     "email": "john@example.com",
     "age": 30
   }
   ```
   Or insert multiple records:
   ```json
   [
     { "name": "John", "email": "john@example.com" },
     { "name": "Jane", "email": "jane@example.com" }
   ]
   ```

### ✏️ Update Data

Modify existing records:

1. **Table Name**: Target table
2. **Filter**: Specify which records to update (required)
   - Example: `id=eq.1`
3. **JSON Data**: Fields to update
   ```json
   {
     "name": "Jane Doe",
     "status": "active"
   }
   ```

### 🗑️ Delete Data

Remove records from tables:

1. **Table Name**: Target table
2. **Filter**: Specify which records to delete (required)
   - Example: `id=eq.1`
3. **Confirmation**: Safety prompt before deletion

⚠️ **Warning**: Deletions are permanent and cannot be undone!

### ⚡ RPC Functions

Execute PostgreSQL functions:

1. **Function Name**: Name of the stored procedure
2. **Parameters**: JSON object with function parameters
   ```json
   {
     "param1": "value1",
     "param2": 123
   }
   ```
3. Use `{}` for functions with no parameters

### 🔐 Authentication

**Sign Up**:

- Enter email and password
- User receives confirmation email
- Check inbox to verify account

**Sign In**:

- Enter credentials
- Receive access token
- Token stored automatically for authenticated requests

**Get Current User**:

- Requires active session (signed in)
- Displays user information and metadata

## 🔧 PostgREST Filter Operators

Common filter operators for querying data:

| Operator | Description              | Example                      |
| -------- | ------------------------ | ---------------------------- |
| `eq`     | Equals                   | `id=eq.1`                    |
| `neq`    | Not equals               | `status=neq.inactive`        |
| `gt`     | Greater than             | `age=gt.18`                  |
| `gte`    | Greater than or equal    | `price=gte.100`              |
| `lt`     | Less than                | `age=lt.65`                  |
| `lte`    | Less than or equal       | `price=lte.1000`             |
| `like`   | Pattern match            | `name=like.*John*`           |
| `ilike`  | Case-insensitive pattern | `email=ilike.*@GMAIL.COM`    |
| `is`     | Check for exact value    | `deleted=is.null`            |
| `in`     | In list                  | `status=in.(active,pending)` |

## 🔒 Security Considerations

⚠️ **Important Security Notes**:

1. **Anon Key Exposure**: The anon key is meant to be public but has limited permissions
2. **Row Level Security (RLS)**: Always enable RLS on your Supabase tables
3. **Production Use**: For production, implement proper authentication and authorization
4. **Token Storage**: Tokens are stored in localStorage (client-side)
5. **HTTPS Only**: Always use this tool over HTTPS in production
6. **Sensitive Data**: Don't store service role keys in the client

### Best Practices:

- Use this tool for development and testing
- Enable Row Level Security on all tables
- Use the anon key, not the service role key
- Implement proper policies in Supabase
- For pentesting, ensure you have proper authorization

## 🎯 Use Cases

### Development

- Rapid prototyping and testing
- Database exploration
- API endpoint testing
- Schema validation

### Testing

- Manual QA testing
- Data verification
- API behavior testing
- Authentication testing

### Penetration Testing

- API security assessment
- Permission testing
- Authentication bypass testing
- Data access verification

⚠️ **Note**: Always ensure you have proper authorization before performing security testing.

## 🐛 Troubleshooting

### Connection Issues

- Verify Supabase URL is correct (format: `https://xxx.supabase.co`)
- Check anon key is valid
- Ensure project is not paused
- Check browser console for errors

### Authentication Errors

- Verify email confirmation is complete
- Check if email auth is enabled in Supabase
- Ensure access token is valid
- Try clearing token and signing in again

### Query Errors

- Verify table name spelling
- Check column names exist
- Ensure RLS policies allow access
- Validate JSON syntax for inserts/updates

### CORS Errors

- This tool makes direct API calls from the browser
- CORS should be handled by Supabase automatically
- If issues persist, check Supabase CORS settings

## 💡 Tips and Tricks

1. **Use the API Explorer First**: Discover tables and functions before querying
2. **Save Filters**: Common filters can be saved in browser bookmarks
3. **JSON Validation**: Use browser dev tools to validate JSON before submitting
4. **Batch Operations**: Use array format in Insert to add multiple records
5. **Collapsible Results**: Click response headers to collapse/expand large JSON

## 🔄 Updates and Maintenance

This tool is self-contained in a single HTML file:

- No dependencies to update
- No build process required
- Works offline (after initial load of Tailwind CSS)
- Can be versioned with git

## 📝 API Reference

Based on PostgREST and Supabase APIs:

- [PostgREST Documentation](https://postgrest.org/)
- [Supabase REST API](https://supabase.com/docs/guides/api)
- [Supabase Auth API](https://supabase.com/docs/reference/javascript/auth-api)

## 🤝 Contributing

Feel free to submit issues and enhancement requests!

## 📄 License

This project is open source and available for personal and commercial use.

## ⚠️ Disclaimer

This tool is provided as-is for development, testing, and authorized security assessment purposes. Users are responsible for ensuring they have proper authorization before accessing any database or performing security testing. The authors are not responsible for any misuse or damage caused by this tool.

---

**Made with ❤️ for Supabase developers and security researchers**
