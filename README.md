🦀 Rust Extract Links

A Rust project that demonstrates how to fetch web page content and extract hyperlinks from HTML using asynchronous requests and HTML parsing.

This project combines networking and parsing concepts by retrieving a webpage, processing its HTML structure, and extracting all available links.

⸻

✨ Features

* Fetch webpage content asynchronously
* Send HTTP requests using Reqwest
* Parse HTML documents
* Extract hyperlinks from <a> tags
* Handle asynchronous execution with Tokio
* Error handling using Anyhow

⸻

🚀 Project Overview

The application retrieves a webpage and scans its HTML structure to find all available links.

Workflow:

Application
      ↓
Send HTTP Request
      ↓
Receive HTML Response
      ↓
Parse HTML Document
      ↓
Find <a> Tags
      ↓
Extract href Links

⸻

🛠 Tech Stack

* Rust 🦀
* Tokio
* Reqwest
* Select
* Anyhow

⸻

📦 Dependencies

[dependencies]
reqwest = { version = "0.12", features = ["json"] }
tokio = { version = "1", features = ["full"] }
anyhow = "1.0"
select = "0.6.1"

⸻

💻 Example Code

use select::document::Document;
use select::predicate::Name;
use anyhow::Result;
#[tokio::main]
async fn main() -> Result<()> {
    let html = reqwest::get("https://example.com")
        .await?
        .text()
        .await?;
    Document::from(html.as_str())
        .find(Name("a"))
        .filter_map(|n| n.attr("href"))
        .for_each(|x| println!("{}", x));
    Ok(())
}

⸻

▶ Running the Project

Clone the repository:

git clone <repository-url>

Move into the project:

cd Rust-Extract-Links

Run:

cargo run

⸻

🎯 Learning Goals

This project helped me explore:

✅ Async programming in Rust
✅ Web requests with Reqwest
✅ HTML parsing
✅ Data extraction techniques
✅ Error handling
✅ Rust ecosystem tooling

⸻

🚀 Future Improvements

* Support extracting images and metadata
* Save extracted links into files
* Filter links by domain
* Build a CLI version
* Crawl multiple pages

⸻

Built with 🦀 + web scraping + curiosity
