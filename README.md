# CipherShare

**CipherShare** is a secure, open-source "burn after reading" secret sharing application. It allows you to share sensitive information (like passwords, API keys, or private messages) securely via a link that self-destructs after being viewed once.

<img width="1919" height="905" alt="Screenshot 2026-01-11 091425" src="https://github.com/user-attachments/assets/fff40c57-fa19-4ff6-97d5-99a8db6a0c84" />

## Features

- **Burn After Reading**: Secrets are permanently deleted from the database immediately after they are accessed.
- **Secure Encryption**: Uses AES-256 encryption to protect secrets at rest.
- **No Logs**: We do not track who accessed what secret.
- **Simple UI**: Clean, modern interface for quick sharing.
- **Open Source**: Verify the code yourself and host it privately.

## Technologies Used

- **Backend**: Java 21, Spring Boot 3.x
- **Frontend**: HTML5, CSS3 (Custom Design), JavaScript (Vanilla)
- **Database**: H2 (In-memory for dev) or configured secure DB
- **Build Tool**: Maven

## Getting Started

### Prerequisites

- Java 21 or higher installed.

### Running Locally

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/yourusername/Cipher-Share.git
    cd cipher-share-api
    ```

2.  **Run the application**:
    On Linux/Mac:
    ```bash
    ./mvnw spring-boot:run
    ```
    On Windows:
    ```powershell
    .\mvnw spring-boot:run
    ```

3.  **Access the app**:
    Open your browser and navigate to: `http://localhost:8080` (or `9090` if configured).

## Usage

1.  Enter your secret in the text area.
2.  Click **Generate Secure Link**.
3.  Copy the generated link and send it to the recipient.
4.  Once the recipient opens the link, the secret is shown and **immediately destroyed**.

## API Documentation

### Create Secret
`POST /api/secrets`
- **Body**: `{ "secret": "your-secret-text" }`
- **Response**: `{ "id": "unique-uuid", "link": "..." }`

### Retrieve Secret
`GET /api/secrets/{id}`
- **Response**: `{ "secret": "your-secret-text" }`
- **Note**: This mimics the "burn" action. Second identical request returns 404.

## License

Distributed under the MIT License. See `LICENSE` for more information.
