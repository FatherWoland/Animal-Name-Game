# AWS Console Setup Guide for Speech Recognition Test

Since you're already logged into AWS, here's how to set it up through the console:

## Step 1: Create S3 Bucket

1. Go to **S3** in AWS Console
2. Click **Create bucket**
3. Bucket name: `animal-name-game-speech-test` (or any unique name)
4. Region: Choose your preferred region
5. **Uncheck** "Block all public access" (we need public access for website hosting)
6. Acknowledge the warning about public access
7. Click **Create bucket**

## Step 2: Enable Static Website Hosting

1. Click on your new bucket
2. Go to **Properties** tab
3. Scroll to **Static website hosting**
4. Click **Edit**
5. Enable static website hosting
6. Index document: `index.html`
7. Save changes

## Step 3: Set Bucket Policy

1. Go to **Permissions** tab
2. Scroll to **Bucket policy**
3. Click **Edit**
4. Paste this policy (replace `YOUR-BUCKET-NAME` with your actual bucket name):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
        }
    ]
}
```

5. Save changes

## Step 4: Upload Files

1. Go to **Objects** tab
2. Click **Upload**
3. Drag and drop these files:
   - `index.html`
   - `diagnostics.html`
   - `README.md` (optional)
4. Click **Upload**

## Step 5: Test S3 Website (HTTP only)

Your site is now available at:
`http://YOUR-BUCKET-NAME.s3-website-REGION.amazonaws.com`

**Note**: This is HTTP only. For HTTPS (required for Speech API), continue to CloudFront.

## Step 6: Create CloudFront Distribution (for HTTPS)

1. Go to **CloudFront** in AWS Console
2. Click **Create distribution**
3. **Origin domain**: Choose your S3 bucket from the dropdown
4. **Origin path**: Leave empty
5. **Name**: Auto-filled
6. **S3 bucket access**: "Yes use OAI" (recommended)
   - Click **Create new OAI**
   - **Yes, update the bucket policy**
7. **Viewer protocol policy**: "Redirect HTTP to HTTPS"
8. **Default root object**: `index.html`
9. Click **Create distribution**

## Step 7: Wait and Access

- CloudFront takes 15-20 minutes to deploy globally
- Your HTTPS URL will be: `https://[distribution-id].cloudfront.net`
- You can find this in the CloudFront distributions list

## Alternative: GitHub Pages (Easier!)

Since you already have the GitHub repo, this might be simpler:

1. Go to https://github.com/FatherWoland/Animal-Name-Game
2. Click **Settings**
3. Scroll to **Pages** (left sidebar)
4. Source: Deploy from a branch
5. Branch: `master` / `/ (root)`
6. Click **Save**
7. Your site will be at: https://fatherwoland.github.io/Animal-Name-Game/

GitHub Pages includes HTTPS automatically!