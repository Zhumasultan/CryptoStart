<<<<<<< HEAD
# CryptoStart: Cryptocurrency Educational Platform

## Project Overview

CryptoStart is an interactive educational platform designed to introduce beginners, students, and crypto investors to the world of cryptocurrency, blockchain technology, and decentralized finance (DeFi). The platform includes real-time cryptocurrency prices, an AI Assistant for quick answers to crypto questions, and easy access to learning resources.

## Technologies Used

- Web Server: Apache2 (Ubuntu 22.04 LTS on AWS EC2)
- Backend: PHP 8.1 (for future expansion, if needed)
- Frontend: HTML, CSS, JavaScript (for frontend UI)
- Crypto Widgets: TradingView for live price tracking of Bitcoin, Ethereum, Solana, Binance Coin, XRP, and Cardano
- AI Assistant: Chatbase-powered AI assistant integrated into the website
- SSL/TLS: Secured with Let's Encrypt SSL certificate for HTTPS access

## Features

- Real-time Crypto Price Tracker: Track live prices of major cryptocurrencies such as Bitcoin, Ethereum, Binance Coin, etc.
- AI Crypto Assistant: An AI-powered assistant that answers crypto-related questions.
- Educational Resources: A comprehensive collection of facts, articles, and tools to learn about crypto.
- Free to Learn: All resources available free of charge.
- Fully responsive modern black-gold-white layout
- SSL + DNS setup via AWS + Namecheap

## How to Use

To access the CryptoStart platform, simply visit: [cryptostart.cc](https://cryptostart.cc)

- View live cryptocurrency prices on the main page.
- Interact with the AI Assistant for questions.
- Browse through interesting facts about cryptocurrencies in the "Awesome Facts" section.
- Learn about blockchain and cryptocurrency in detail, free of charge.

## Project Development Timeline

- Feb 28, 2025: Initial project setup and AWS EC2 deployment.
- Mar 1, 2025: Integrated SSL/TLS (Let's Encrypt), DNS setup.
- Mar 10, 2025: Applied StartBootstrap Agency template, customized design for crypto project.
- Mar 17, 2025: Added Crypto Price Tracker widgets for major cryptocurrencies.
- Mar 26, 2025: Added "Features" section with AI Assistant, Live Price Tracker, and Free to Learn.
- Apr 3, 2025: Replaced "Team" section with "Crypto Blog" and linked to external cryptocurrency articles.
- Apr 4, 2025: Fixed broken navbar links and improved design.
- Apr 5, 2025: Finalized contact form and polished website design.
- Apr 10, 2025: Final revisions, video explainer recorded, and website submitted for review.

## License

The project is licensed under the *Creative Commons Attribution-ShareAlike 4.0 (CC BY-SA 4.0)* license. You can freely copy, modify, and redistribute the project under the same license.

## GitHub Repository

[GitHub - CryptoStart](https://github.com/Zhumasultan/cryptostart)

## How to replicate the project

 To replicate this project, follow the detailed instructions below. This cryptocurrency education platform was developed using a customized HTML/CSS/JS template, deployed on an AWS EC2 instance with a functional domain name, SSL certificate, AI assistant, and real-time crypto widgets. All necessary steps are included for full replication.

Create an AWS EC2 instance via the AWS Management Console. Choose Ubuntu 22.04 LTS as the operating system and t3.micro as the instance type. Generate or use an existing PEM key for SSH access. Under network settings, allow inbound rules for SSH (port 22), HTTP (port 80), and HTTPS (port 443) from 0.0.0.0/0.

Connect to your instance using SSH: ssh -i "path/to/your-key.pem" ubuntu@your-ec2-public-ip

Update the system and install Apache: sudo apt update && sudo apt upgrade -y
sudo apt install apache2 -y

(Optional) Enable UFW firewall and allow Apache: sudo ufw allow 'Apache Full'
sudo ufw enable

Upload your website files to the server using SCP or rsync. Place all HTML, CSS, JS, and image files into /var/www/html/. Example: scp -i "your-key.pem" -r ./local-folder/* ubuntu@your-ip:/var/www/html/

Assign correct permissions to the Apache server: sudo chown -R www-data:www-data /var/www/html/

Purchase a domain name (this project used cryptostart.cc) and configure DNS A-record to point to your server’s public IP address via your registrar’s control panel (e.g., Namecheap). Wait for DNS propagation to complete.

Install Certbot and activate SSL using Let’s Encrypt: sudo apt install snapd -y
sudo snap install core && sudo snap refresh core
sudo snap install --classic certbot
sudo certbot --apache -d yourdomain.com -d www.yourdomain.com

Visit https://yourdomain.com and verify HTTPS is working without errors. Optionally test via ssllabs.com/ssltest.

Add real-time crypto price widgets. Go to TradingView’s Crypto Widget Generator and configure widgets for BTC, ETH, SOL, BNB, XRP, and ADA. Copy the script tags and embed them into the “Live Prices” section of your HTML (formerly the portfolio section).

Integrate an AI assistant. Create a bot on https://www.chatbase.co/. Configure it with your desired settings. After setup, copy the provided JavaScript embed code and paste it before the </body> tag of your HTML. This enables the floating chatbot on your site.

(Optional) Enhance your project with a useful JavaScript snippet such as a dynamic clock, custom toggle theme switcher, or client-side script that improves usability or experience. Document its purpose clearly in your code and in the README file.

Make sure your project is live and fully accessible via both IP and domain name. Open your site in different browsers and test all features (chatbot, SSL, widgets, navigation).

Use Git for version control. In your project folder: git init
git add .
git commit -m "Initial commit"
Create a GitHub repo and push your code there using: git remote add origin https://github.com/yourusername/yourrepo.git
git push -u origin master

Create a README.md file and include all key project information: summary, steps taken, tools used (Apache, AWS EC2, Let’s Encrypt, Chatbase), license used, customizations made to the HTML template, and instructions for replication.

This sequence allows anyone to recreate the CryptoStart platform from scratch with full functionality, including cloud deployment, domain configuration, SSL security, educational layout, AI assistant, and live crypto market data.

## DNS and SSL Configuration

To ensure professional accessibility and secure communication, this project includes a custom domain and full HTTPS encryption.

A domain name was registered via Namecheap: cryptostart.cc

DNS A-record was configured in the Namecheap DNS settings to point to the public IP address of the AWS EC2 instance (e.g., 51.21.164.51). This record ensures that when users visit cryptostart.cc, they are directed to the hosted server.

DNS propagation was verified using tools like dnschecker.org and confirmed to be fully functional within a few hours.

To secure the website, Let’s Encrypt SSL/TLS encryption was installed using Certbot. Apache was automatically configured to redirect all HTTP traffic to HTTPS. Commands used: sudo apt install snapd -y
sudo snap install core && sudo snap refresh core
sudo snap install --classic certbot
sudo certbot --apache -d cryptostart.cc -d www.cryptostart.cc

SSL functionality was verified using browser inspection and external services (e.g., Qualys SSL Labs). The site has no certificate errors and loads securely over HTTPS.

Automatic renewal of the SSL certificate is handled by Certbot's system timer. No manual renewal is needed for 90 days.

These steps ensure the domain is properly mapped to the cloud instance and that all traffic is securely encrypted using industry-standard SSL/TLS protocols.

## Script Documentation

This project integrates multiple custom and third-party scripts that significantly improve the functionality, usefulness, and educational value of the website. Below are the scripts used, their purpose, implementation details, and the steps taken to ensure clarity, modularity, and replicability.

1. TradingView Live Cryptocurrency Price Widgets

Purpose:
To provide users with real-time updates of top cryptocurrencies directly on the homepage in a visually engaging format, without requiring page refresh or redirection.

Cryptocurrencies Covered:

Bitcoin (BTC)

Ethereum (ETH)

Solana (SOL)

Binance Coin (BNB)

Ripple (XRP)

Cardano (ADA)

Script Source:
All widgets were embedded using the official TradingView Widget API:
🔗 https://www.tradingview.com/widget/crypto-mkt-overview/

Integration Method:
Each coin widget was inserted as a separate block using the following structure:

<div class="portfolio-item">
  <h4 class="text-center" style="color:gold;">Bitcoin (BTC)</h4>
  <div id="tradingview_btc" style="height:220px"></div>
</div>

The widgets are powered using TradingView’s base JavaScript library:


<script type="text/javascript" src="https://s3.tradingview.com/tv.js"></script>

A custom function waits for the TradingView script to fully load and then initializes each widget dynamically using JavaScript, allowing them to render cleanly within the “Live Prices” section of the site.

Placement:
Inserted inside /index.html in the <section id="portfolio"> block, each with appropriate cryptocurrency label and placement within the Bootstrap grid layout.

2. Chatbase AI Crypto Assistant Script

Purpose:
To enhance the user experience by offering a built-in AI assistant capable of answering questions about cryptocurrency, blockchain, DeFi, and NFTs. The assistant improves user retention, adds interactivity, and aligns with the educational goals of the site.

Script Source:
The AI assistant is powered by Chatbase (Google-based LLM engine) and was configured with custom welcome prompts, profile picture, and example queries.

Integration Method:
The floating assistant was added using Chatbase’s official embed code:

<script>
  window.chatbaseConfig = {
    chatbotId: "Ue8mO0RIX78yngP0rmdiR"
  }
</script>
<script src="https://www.chatbase.co/embed.min.js" chatbotId="Ue8mO0RIX78yngP0rmdiR" defer></script>

Placement:
Inserted just before the closing </body> tag of the HTML document to ensure the rest of the content loads first and to avoid render-blocking. The assistant icon appears at the bottom right corner of all pages.

Chat Features:

Natural language processing

Custom branding and message

Instant answers to beginner-level crypto queries

Based on user-friendly API connection to Chatbase backend

Best Practices and Validation

All scripts were tested for compatibility with Apache2 on Ubuntu 22.04 LTS.

HTML structure was validated using W3C Validator.

No render-blocking issues were detected.

The scripts gracefully degrade if JavaScript is disabled (i.e., they do not crash the site).

Summary

Both the TradingView and Chatbase scripts were deliberately selected and thoughtfully integrated into the project to support the website’s goal of being an accessible, educational, and real-time crypto learning platform. The scripts are fully documented, publicly sourced, and can be easily replicated or extended by anyone reviewing the project.

## Script Verifiable Output

Both main scripts in this project produce clear, verifiable, and visual output directly on the website's homepage:

1. TradingView Widgets:
   - The live cryptocurrency price widgets display real-time charts for BTC, ETH, SOL, BNB, XRP, and ADA.
   - These widgets are publicly visible and interactive for all users without login or delay.
   - The price data is updated automatically, and each widget includes coin name headings for clarity.

2. Chatbase AI Assistant:
   - A persistent chatbot icon is always visible in the bottom-right corner of the website.
   - Users can interact directly with the assistant by clicking the icon and asking questions related to cryptocurrency.
   - The assistant replies instantly and its responses appear directly on the screen, making it easily testable and verifiable.

Both scripts were tested using multiple browsers and devices, ensuring consistent and visible behavior across platforms.

## Script Fit and Purpose

Both integrated scripts were selected specifically for their direct relevance to the website’s functionality and learning goals:

- TradingView Widgets directly support the project’s mission to educate users about cryptocurrencies by visually presenting live price data of the most relevant coins. This helps beginners immediately connect educational content with real-world market behavior.

- Chatbase AI Assistant provides instant guidance to users, answering basic and advanced questions about blockchain, Bitcoin, NFTs, and more. It mimics human support, enhances user engagement, and helps retain visitors longer on the platform.

Together, these scripts enhance the website’s practical value, interactivity, and credibility, and clearly contribute to the site's purpose as a free crypto education platform.



I also want to add that I put my soul into this site and made the best design, and now I plan to use it not only for studying, but also for real purposes. I also plan to improve it, find users and launch advertising for monetization and earnings.
=======
# CryptoStart
>>>>>>> ce0d7d8147c5c181e9236c91498e31bc6de7d461
