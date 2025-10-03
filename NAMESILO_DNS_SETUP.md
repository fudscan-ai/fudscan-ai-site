# NameSilo DNS Configuration for GitHub Pages

Follow these steps to point your fudscan.ai domain from NameSilo to GitHub Pages.

## Step 1: Access NameSilo DNS Manager

1. Log in to your NameSilo account at https://www.namesilo.com
2. Go to **Domain Manager**
3. Find **fudscan.ai** in your domain list
4. Click on the **DNS** icon (blue globe icon) next to the domain

## Step 2: Configure DNS Records

You need to add the following DNS records:

### A Records (for apex domain)

Delete any existing A records and add these four A records pointing to GitHub's servers:

```
Type: A
Host: @
Value: 185.199.108.153
TTL: 3600

Type: A
Host: @
Value: 185.199.109.153
TTL: 3600

Type: A
Host: @
Value: 185.199.110.153
TTL: 3600

Type: A
Host: @
Value: 185.199.111.153
TTL: 3600
```

### CNAME Record (for www subdomain)

```
Type: CNAME
Host: www
Value: <your-github-username>.github.io
TTL: 3600
```

Replace `<your-github-username>` with your actual GitHub username (the repository owner).

## Step 3: GitHub Repository Settings

1. Go to your GitHub repository: https://github.com/jenks/fudscan-ai-site
2. Navigate to **Settings** → **Pages**
3. Under **Source**, select the branch you want to deploy (usually `main`)
4. Under **Custom domain**, enter: `fudscan.ai`
5. Wait for DNS check to complete (may take a few minutes to a few hours)
6. Once verified, check **Enforce HTTPS**

## Step 4: Verify Configuration

DNS propagation can take anywhere from a few minutes to 48 hours. You can check the status using:

- **DNS Checker**: https://dnschecker.org
- **WhatsMyDNS**: https://www.whatsmydns.net
- **Command Line**: `dig fudscan.ai` or `nslookup fudscan.ai`

## Step 5: Test Your Site

Once DNS propagation is complete, visit:
- https://fudscan.ai
- https://www.fudscan.ai

Both should load your GitHub Pages site with HTTPS.

## Troubleshooting

### DNS Not Propagating
- Wait up to 48 hours for full global propagation
- Clear your browser cache and DNS cache
- Try accessing from a different network/device

### HTTPS Not Working
- Make sure DNS has fully propagated first
- Uncheck and re-check "Enforce HTTPS" in GitHub Pages settings
- Wait 5-10 minutes and try again

### Custom Domain Not Verifying in GitHub
- Double-check all A records are correct
- Ensure CNAME file exists in your repository root with content: `fudscan.ai`
- Check that no conflicting DNS records exist (like old A records)

## Important Notes

- The `CNAME` file in your repository root is essential - it tells GitHub Pages what custom domain to use
- GitHub Pages automatically handles SSL certificates via Let's Encrypt
- Changes to DNS can take time to propagate globally
- Always use HTTPS for production sites

## Summary of DNS Records

After setup, your NameSilo DNS should look like this:

| Type  | Host | Value                           | TTL  |
|-------|------|---------------------------------|------|
| A     | @    | 185.199.108.153                 | 3600 |
| A     | @    | 185.199.109.153                 | 3600 |
| A     | @    | 185.199.110.153                 | 3600 |
| A     | @    | 185.199.111.153                 | 3600 |
| CNAME | www  | <username>.github.io            | 3600 |

Replace `<username>` with your GitHub username.
