# MongoDB Atlas Setup Guide

## Step 1: Create MongoDB Atlas Account

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Click "Sign Up" and create a free account
3. Verify your email address

## Step 2: Create a Cluster

1. After login, click "Create a Deployment"
2. Choose **Free Tier** (M0 cluster)
3. Select your preferred region (closest to you)
4. Click "Create Deployment"

## Step 3: Create a Database User

1. Go to "Database Access" in left sidebar
2. Click "Add New Database User"
3. Choose **Password** authentication
4. Enter username: `examadmin`
5. Enter a strong password (save this!)
6. Click "Add User"

## Step 4: Add IP Whitelist

1. Go to "Network Access" in left sidebar
2. Click "Add IP Address"
3. Click "Allow Access from Anywhere" (for development)
   - Or add your specific IP: `0.0.0.0/0`
4. Click "Confirm"

## Step 5: Get Connection String

1. Go to your cluster page
2. Click "Connect" button
3. Select "Drivers" option
4. Choose **Node.js** and version **4.x or higher**
5. Copy the connection string

**Connection String Format:**
```
mongodb+srv://examadmin:PASSWORD@cluster-name.mongodb.net/database-name?retryWrites=true&w=majority
```

## Step 6: Update Environment Variables

Replace `PASSWORD` and `cluster-name` in the string, then update your `.env` file:

```dotenv
PORT=5000
MONGODB_URI=mongodb+srv://examadmin:YOUR_PASSWORD@cluster-name.mongodb.net/online-exam-system?retryWrites=true&w=majority
JWT_SECRET=supersecretkey123
NODE_ENV=development
```

## Step 7: Test Connection

```bash
cd backend
npm start
```

You should see: "Connected to MongoDB" in the console.

## Security Best Practices

1. **Never commit `.env` file to GitHub** (already in .gitignore ✓)
2. **Use strong passwords** for database users
3. **Restrict IP access** in production (don't use 0.0.0.0/0)
4. **Use environment variables** for sensitive data
5. **Enable IP Whitelist** for known servers only

## MongoDB Atlas Free Tier Limits

- **Storage**: 512 MB
- **Connections**: Max 100 concurrent
- **No backup** (paid only)
- **Single replica set** (no sharding)

For production, upgrade to paid tier.

## Troubleshooting

**Connection Timeout**
- Check IP whitelist settings
- Verify password is correct
- Check database name in connection string

**Authentication Failed**
- Verify username and password
- Make sure @ symbol is URL encoded if special char in password
- Example: `p@ss` → `p%40ss`

**Cluster Not Found**
- Copy connection string again
- Check cluster name is correct
- Verify cluster is running

## Useful MongoDB Atlas Commands

```bash
# View cluster status
# Go to Dashboard → Your Cluster

# Monitor performance
# Go to Metrics tab

# View logs
# Go to Logs tab

# Manage collections
# Go to Browse Collections
```

## Connection String Examples

**Local MongoDB:**
```
mongodb://localhost:27017/online-exam-system
```

**MongoDB Atlas (Cloud):**
```
mongodb+srv://examadmin:password@cluster0.abc123.mongodb.net/online-exam-system?retryWrites=true&w=majority
```

---

For more help: [MongoDB Atlas Documentation](https://docs.atlas.mongodb.com/)
