---
title: "Amazon Scraping Options: APIs, Tools & Case Studies"
description: "A practical rundown of ways to get data out of Amazon — the official Product Advertising / Creators API, commercial scraping services like Bright Data, open-source scrapers, and the research datasets built on scraped Amazon reviews."
image: https://api.imageee.com/bold?text=PHP:%20Amazon%20Scraping%20Options&bg_image=https://images.unsplash.com/photo-1542762933-ab3502717ce7
---

# Amazon Scraping Options

## Official Route: Amazon's Affiliate APIs

- **[Creators API](https://affiliate-program.amazon.com/creatorsapi/docs/en-us/introduction)** — Amazon Associates' current API for product data (the older Product Advertising API 5.0 is being phased out, deprecated May 2026). Free for approved Associates, scoped to affiliate/product-linking use cases rather than bulk data extraction.

## Commercial Scraping Services

- **[Bright Data — Amazon Scraper API](https://brightdata.com/products/web-scraper/amazon)** — managed endpoints for products, search results, reviews and seller data, returned as structured JSON; handles proxies, CAPTCHAs and page rendering.
- **[Apify — Amazon Product Scraper](https://apify.com/junglee/amazon-crawler)** — a widely-used pay-per-result actor for product, price and review data by search or URL.
- **[RapidAPI — Real-Time Amazon Data](https://rapidapi.com/letscrape-6bRBa3QguO5/api/real-time-amazon-data)** — one of the more popular RapidAPI marketplace listings, covering products, reviews, best-sellers and seller data.

Priced on usage and limited to publicly visible data — check current terms before committing to a plan.

## Open-Source Options

- **[amazon-scraper-python](https://github.com/tducret/amazon-scraper-python)** — a non-official Python client for reading basic product info from Amazon listings.
- **PHPScraper** itself can fetch and parse public Amazon product pages, but Amazon's bot detection means this is best combined with rotating proxies for anything beyond occasional lookups.

## Real-World Use Cases & Case Studies

- **[Amazon Reviews'23](https://amazon-reviews-2023.github.io/)** — a large-scale, publicly released dataset (hundreds of millions of reviews and product metadata) built from scraped Amazon data by UCSD's McAuley Lab. It's become a standard benchmark for recommender-systems and NLP research — a good example of scraped e-commerce data powering years of downstream academic work.
