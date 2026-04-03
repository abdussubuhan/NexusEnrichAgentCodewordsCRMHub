# Deployment & Installation Guide

This guide will walk you through setting up the Codewords NexusEnrich Agent locally, formatting your environment variables, and deploying it to a production host like Vercel.

## 1. Local Installation

Before you begin, ensure you have **Node.js 18+** installed on your machine.

1. Unzip the project folder.
2. Open your terminal and navigate to the project directory:
   ```bash
   cd codewords-agent
   ```
3. Install the dependencies using npm:
   ```bash
   npm install
   ```
4. Copy the environment variables template and configure your keys:
   ```bash
   cp .env.example .env.local
   ```
5. Run the local development server:
   ```bash
   npm run dev
   ```
6. Open `http://localhost:3000` in your browser.

## 2. Environment Variables

Open `.env.local` and populate the required fields. 
The system requires your destination CRM webhook URL, your CRM REST API Bearer Token, and any scraper/LLM keys (like OpenAI) you intend to utilize in the Enrichment Node.

## 3. Production Deployment (Vercel)

This application is built with Next.js, and natively deploys to Vercel with zero-configuration.

1. Push your repository to **GitHub** (Ensure your `.env.local` is ignored and safely backed up).
2. Log into [Vercel](https://vercel.com/) and click "Add New Project".
3. Import your GitHub repository.
4. Expand the **Environment Variables** tab before deploying. Copy every key from your `.env.local` into the Vercel dashboard.
5. Click **Deploy**.

Within 2 minutes, your Control Panel Dashboard and API Route listeners will be live globally.
