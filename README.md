<div align="center">

<img src="./public/logo.png" width="160" height="160" alt="Tavily Search Plugin">

# LobeChat Tavily AI Search Plugin

**🔍 AI-Powered Real-Time Web Search Engine for LobeChat**

[![][vercel-shield]][vercel-url]
[![][license-shield]][license-url]
[![][github-stars-shield]][github-stars-url]
[![][github-forks-shield]][github-forks-url]

[English](./README.md) · [简体中文](./README.zh-CN.md)

**Empower your AI conversations with intelligent, real-time web search capabilities**

[Get Started](#-quick-start) · [Features](#-key-features) · [Deployment](#-deployment-guide) · [Documentation](#-documentation)

<img src="./public/example.png" width="800" alt="Example Screenshot">

</div>

<br/>

## 📖 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Quick Start](#-quick-start)
- [Deployment Guide](#-deployment-guide)
- [Technical Stack](#-technical-stack)
- [API Reference](#-api-reference)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Acknowledgments](#-acknowledgments)

<br/>

## 🌟 Overview

The **LobeChat Tavily AI Search Plugin** seamlessly integrates [Tavily AI's](https://tavily.com/) cutting-edge search API into [LobeChat](https://github.com/lobehub/lobe-chat), transforming your AI assistant into an intelligent research companion with real-time access to web information.

### Why Tavily AI Search?

<table>
<tr>
<td width="50%">

**🎯 Optimized for LLMs**
- Search results specifically formatted for language models
- Reduces AI hallucinations with verified data
- Enhanced context for better decision-making

</td>
<td width="50%">

**⚡ Lightning Fast**
- Sub-second response times
- Real-time information retrieval
- Efficient API performance

</td>
</tr>
<tr>
<td width="50%">

**💎 Developer Friendly**
- 1,000 free searches/month
- No credit card required
- Simple integration process

</td>
<td width="50%">

**🔒 Privacy & Security**
- Private deployment support
- Secure API key management
- Full control over data flow

</td>
</tr>
</table>

<br/>

## ✨ Key Features

- **🔍 Intelligent Search**: Leverage Tavily's AI-optimized search engine designed specifically for LLM applications
- **📊 Rich Results**: Get comprehensive, structured search results with relevant context
- **🎨 Beautiful UI**: Modern, responsive interface built with Next.js 15 and React 19
- **⚙️ Easy Configuration**: Simple setup process with intuitive settings management
- **🚀 One-Click Deploy**: Deploy your own instance to Vercel in seconds
- **🔐 Secure by Default**: API key encryption and secure credential management
- **🌐 Multi-language**: Support for both English and Chinese interfaces
- **📱 Responsive Design**: Optimized for desktop and mobile experiences

<br/>

## 🚀 Quick Start

### Prerequisites

Before you begin, ensure you have:
- A [LobeChat](https://lobehub.com/) instance (cloud or self-hosted)
- A [Tavily API](https://tavily.com/) account

### Step 1: Obtain Your Tavily API Key

1. **Sign Up**: Visit [tavily.com](https://tavily.com/) and create a free account
2. **Generate Key**: Navigate to your dashboard and create a new API key
3. **Save Key**: Copy and securely store your API key

> 💡 **Tip**: You get **1,000 free searches per month** without requiring a credit card!

### Step 2: Install the Plugin in LobeChat

#### Option A: Use Official Deployment

1. Open your LobeChat instance
2. Navigate to **Plugin Store** → **Custom Plugin** → **Edit Installation File**
3. Add the following URL to **Description File URL**:
   ```
   https://lobe-plugin.composere.com/manifest.json
   ```
4. Click **Install Plugin**
5. Enter your Tavily API key in the plugin settings

#### Option B: Deploy Your Own Instance

For enhanced security and customization, [deploy your own instance](#-deployment-guide).

### Step 3: Start Searching

1. Start a new conversation in LobeChat
2. Enable the Tavily Search plugin
3. Ask questions that require real-time information
4. Watch as your AI assistant retrieves and analyzes current web data

<br/>

## 🛠 Deployment Guide

### Deploy to Vercel (Recommended)

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/dielect/lobechat-tavily-plugin)

1. **Fork & Deploy**
   ```bash
   # Fork this repository
   # Click the "Deploy to Vercel" button above
   # Follow the deployment wizard
   ```

2. **Configure Your Instance**

   Update `public/manifest.json`:
   ```json
   {
     "api": [{
       "url": "https://YOUR_DOMAIN.vercel.app/api/tavily"
     }],
     "ui": {
       "url": "https://YOUR_DOMAIN.vercel.app/search"
     }
   }
   ```

3. **Install in LobeChat**

   Use your custom manifest URL:
   ```
   https://YOUR_DOMAIN.vercel.app/manifest.json
   ```

### Advanced: Custom Gateway Configuration

For advanced users who want to customize the API gateway:

1. Reference `public/manifest-dev.json` as a template
2. Update the `gateway` field:
   ```json
   {
     "gateway": "https://YOUR_CUSTOM_GATEWAY.com"
   }
   ```

### Local Development

```bash
# Clone the repository
git clone https://github.com/dielect/lobechat-tavily-plugin.git
cd lobechat-tavily-plugin

# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build

# Start production server
npm start
```

<br/>

## 🔧 Technical Stack

This plugin is built with modern, cutting-edge technologies:

| Category | Technologies |
|----------|-------------|
| **Framework** | Next.js 15.1.7, React 19 |
| **Language** | TypeScript 5 |
| **Styling** | Tailwind CSS 3.4, tailwindcss-animate |
| **Animation** | Framer Motion 12.4 |
| **UI Components** | Radix UI, Lucide React |
| **API Integration** | Tavily Core SDK 0.3.1 |
| **LobeHub SDKs** | @lobehub/chat-plugin-sdk, @lobehub/chat-plugins-gateway |
| **Build Tool** | Turbopack (Next.js) |

### Architecture Overview

```
┌─────────────────────────────────────────────────────────┐
│                      LobeChat                           │
│  ┌───────────────────────────────────────────────────┐  │
│  │           Plugin Interface                        │  │
│  └────────────────────┬──────────────────────────────┘  │
└───────────────────────┼─────────────────────────────────┘
                        │
                        │ Plugin SDK
                        │
┌───────────────────────▼─────────────────────────────────┐
│          Tavily Search Plugin (This Project)            │
│  ┌─────────────────────────────────────────────────┐    │
│  │  Next.js API Routes (/api/tavily)              │    │
│  │  ┌───────────────────────────────────────────┐ │    │
│  │  │  Authentication & Validation              │ │    │
│  │  └────────────────┬──────────────────────────┘ │    │
│  │                   │                            │    │
│  │  ┌────────────────▼──────────────────────────┐ │    │
│  │  │  Tavily API Integration                   │ │    │
│  │  └────────────────┬──────────────────────────┘ │    │
│  └───────────────────┼─────────────────────────────┘    │
│                      │                                   │
│  ┌───────────────────▼─────────────────────────────┐    │
│  │  UI Component (/search)                         │    │
│  │  • Results Display                              │    │
│  │  • Interactive Interface                        │    │
│  └─────────────────────────────────────────────────┘    │
└───────────────────────┬─────────────────────────────────┘
                        │
                        │ Tavily API
                        │
┌───────────────────────▼─────────────────────────────────┐
│                  Tavily AI Search API                   │
│              https://api.tavily.com                     │
└─────────────────────────────────────────────────────────┘
```

<br/>

## 📚 API Reference

### Search Web Endpoint

**Endpoint**: `POST /api/tavily`

**Description**: Performs advanced web searches using Tavily's search engine API.

**Parameters**:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `query` | string | ✅ Yes | The search query or keywords to look up |

**Example Request**:

```typescript
const response = await fetch('https://lobe-plugin.composere.com/api/tavily', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer YOUR_API_KEY'
  },
  body: JSON.stringify({
    query: 'Latest AI developments 2025'
  })
});

const data = await response.json();
```

**Response Format**:

```typescript
interface SearchResult {
  results: Array<{
    title: string;
    url: string;
    content: string;
    score: number;
  }>;
  query: string;
  responseTime: number;
}
```

<br/>

## 🗺 Roadmap

### 🎯 Planned Features

- [ ] **Enhanced Tavily API Integration**
  - [ ] Support for multiple search types (web, news, academic)
  - [ ] Configurable result length and format
  - [ ] Advanced filtering and sorting options
  - [ ] Domain-specific search capabilities

- [ ] **UI/UX Improvements**
  - [x] ~~Rich result preview with thumbnails~~
  - [ ] Search history management
  - [ ] Bookmarking favorite results
  - [ ] Export results to various formats

- [ ] **Performance Enhancements**
  - [ ] Intelligent caching mechanism
  - [ ] Request debouncing and throttling
  - [ ] Optimized response times
  - [ ] Progressive result loading

- [ ] **Developer Experience**
  - [ ] Comprehensive API documentation
  - [ ] Example integrations and templates
  - [ ] Testing utilities and mocks
  - [ ] Debug mode and logging options

- [ ] **Enterprise Features**
  - [ ] Usage analytics and monitoring
  - [ ] Rate limiting configuration
  - [ ] Multi-user API key management
  - [ ] Webhook notifications

<br/>

## 🤝 Contributing

We welcome contributions from the community! Whether you're fixing bugs, improving documentation, or proposing new features, your help is appreciated.

### How to Contribute

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Development Guidelines

- Follow the existing code style and conventions
- Write clear, descriptive commit messages
- Add tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting PR

### Reporting Issues

Found a bug or have a suggestion? Please [open an issue](https://github.com/dielect/lobechat-tavily-plugin/issues) with:
- A clear, descriptive title
- Detailed description of the issue or feature
- Steps to reproduce (for bugs)
- Expected vs. actual behavior
- Screenshots or code samples (if applicable)

<br/>

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 dielect

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

<br/>

## 🙏 Acknowledgments

This project wouldn't be possible without these amazing tools and communities:

- **[LobeChat](https://github.com/lobehub/lobe-chat)** - The innovative AI chat platform that makes this plugin possible
- **[Tavily AI](https://tavily.com/)** - For providing the powerful, LLM-optimized search API
- **[Vercel](https://vercel.com/)** - For seamless deployment and hosting infrastructure
- **[Next.js](https://nextjs.org/)** - The React framework that powers this application
- **[Tailwind CSS](https://tailwindcss.com/)** - For the beautiful, responsive design system

### Special Thanks

- All contributors who have helped improve this plugin
- The LobeChat community for their support and feedback
- Early adopters and testers who provided valuable insights

<br/>

---

<div align="center">

### Made with ❤️ for the LobeChat Community

**[⬆ Back to Top](#lobechat-tavily-ai-search-plugin)**

[![][back-to-top]](#readme)

</div>

<!-- LINK GROUP -->

[vercel-shield]: https://img.shields.io/badge/Vercel-Deployed-black?style=flat&logo=vercel
[vercel-url]: https://vercel.com
[license-shield]: https://img.shields.io/badge/license-MIT-blue.svg?style=flat
[license-url]: ./LICENSE
[github-stars-shield]: https://img.shields.io/github/stars/dielect/lobechat-tavily-plugin?style=social
[github-stars-url]: https://github.com/dielect/lobechat-tavily-plugin/stargazers
[github-forks-shield]: https://img.shields.io/github/forks/dielect/lobechat-tavily-plugin?style=social
[github-forks-url]: https://github.com/dielect/lobechat-tavily-plugin/network/members
[back-to-top]: https://img.shields.io/badge/-BACK_TO_TOP-black?style=flat-square
