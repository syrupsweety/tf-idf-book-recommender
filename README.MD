# TF-IDF Book Recommender

A real-time book recommendation system that uses **TF-IDF (Term Frequency-Inverse Document Frequency)** and **cosine similarity** to suggest books based on textual content. The app features a web interface accessible via a public URL, automatic reloading of new books, and live updates.

## Overview

This project analyzes full-text `.txt` files of books stored in Google Drive and recommends similar titles by comparing their content using TF-IDF vectors. It runs in Google Colab, exposes a Flask web server, and makes it publicly accessible using `localtunnel`.

Key Features:
- Real-time book loading from a folder
- Auto-detects new or deleted books every 5 seconds
- Simple web UI for searching and viewing recommendations
- Publicly accessible via secure tunnel
- QR code displayed on the page for mobile access
- Displays similarity scores between books

## How It Works

1. **Text Processing**: Loads `.txt` files named in the format `Title by Author.txt`.
2. **Vectorization**: Uses `TfidfVectorizer` with Russian stop words and bigrams.
3. **Similarity Calculation**: Computes cosine similarity between all books.
4. **Dynamic Updates**: Automatically rebuilds the model when books are added or removed.
5. **Web Interface**: Hosted with Flask and exposed via `localtunnel`.

## File Structure Expectation

Place your book `.txt` files in a Google Drive folder (e.g., `/MyDrive/tf-idf/txt`) using this naming convention:

```
War and Peace by Leo Tolstoy.txt
Anna Karenina by Leo Tolstoy.txt
Crime and Punishment by Fyodor Dostoevsky.txt
```


> ⚠️ Files must follow `Title by Author.txt` format for correct parsing.

## ▶️ How to Run

1. Upload and run the notebook's Dynamic + QR section.

2. The system will:
   - Load all books from the specified folder
   - Start a Flask web server on port 5000
   - Expose it publicly using `localtunnel`
   - Print a public URL and password (your IP)

3. Access the web app through the generated link (valid for the session).

## 🌐 Web Interface

Once running, you’ll see output like:

```
🌟 Public URL: https://abcd1234.localtunnel.me
🔐 Access Password (IP): 93.184.216.34
```

Visit the URL to use the interactive recommender:
- Search for any loaded book title
- Get top 5 similar book recommendations
- View similarity scores
- See total book count (auto-updates)

A QR code is shown in the bottom-right corner for easy mobile access.

## 🧩 Dependencies

- Python 3.x
- `numpy`
- `scikit-learn`
- `Flask`
- `google-colab` (for Drive mount)
- `npm` + `localtunnel` (for public access)
- `requests` (for IP detection)

Installed automatically in Colab environment.

## 📚 Example Usage

Input:
```
War and Peace
```

Output:
| # | Title               | Author             | Similarity |
|---|---------------------|--------------------|------------|
| 1 | Anna Karenina       | Leo Tolstoy        | 0.872      |
| 2 | The Death of Ivan Ilyich | Leo Tolstoy | 0.621      |
| 3 | Hadji Murat         | Leo Tolstoy        | 0.583      |

## ❗ Limitations

- Only supports `.txt` files.
- Long texts are truncated to 10,000 words.
- Stop words are currently tailored for Russian — modify if using other languages.
- `localtunnel` may occasionally fail; restart if needed.
- Not designed for production-scale use.
