# GitHub Image Cloud

A professional image hosting service similar to Imgur, which stores images directly inside a GitHub repository.

## Features
- **Upload via Drag & Drop or Clipboard**: Fast and responsive image uploading.
- **GitHub Backend**: No storage costs! Images are optimized and saved to your configured GitHub repository.
- **CDN Powered**: Uses jsdelivr CDN for fast image previewing and sharing.
- **Short Links**: Share your images easily with short links.
- **Analytics**: Keep track of total uploads, views, and bandwidth in a local SQLite database.

## Environment Variables
Create a \`.env\` file in the \`backend\` directory with the following variables:

\`\`\`env
# Required for GitHub Repository access
GITHUB_TOKEN=your-github-personal-access-token
GITHUB_USERNAME=Uviii9p
GITHUB_REPO=ima
GITHUB_BRANCH=main

# Optional
PORT=5000
\`\`\`

### How to get a GitHub Personal Access Token (PAT):
1. Go to your GitHub account settings.
2. Select **Developer settings** from the left sidebar.
3. Click on **Personal access tokens** -> **Tokens (classic)**.
4. Click **Generate new token (classic)**.
5. Give your token a name (e.g., "GitHub Image Cloud").
6. Select the \`repo\` scope to allow it to read and write repository content.
7. Click **Generate token** and copy it into the \`.env\` file as \`GITHUB_TOKEN\`.

## Running Locally

1. Install dependencies for the backend:
\`\`\`bash
cd backend
npm install
\`\`\`

2. Run the Backend:
\`\`\`bash
npm run start
\`\`\`

3. Install dependencies for the frontend:
\`\`\`bash
cd frontend
npm install
\`\`\`

4. Run the Frontend:
\`\`\`bash
npm run dev
\`\`\`

## Deployment

### Frontend (Vercel)
The frontend project is located in the \`frontend\` directory and can be deployed easily with [Vercel](https://vercel.com/):
1. Connect your repository to Vercel.
2. Configure the Build Command to \`npm run build\` and the Build Directory to \`dist\`.
3. Create an environment variable \`VITE_API_URL\` pointing to your deployed backend URL.

### Backend (Render / Railway)
The backend project in the \`backend\` directory can be deployed on Render or Railway:
1. Connect your repository to the service.
2. Setup the start command as \`node server.js\`.
3. Add the required environment variables (especially \`GITHUB_TOKEN\`). Note that since \`better-sqlite3\` stores data in \`analytics.sqlite\`, this file will reset on every deploy unless you use a persistent volume.
