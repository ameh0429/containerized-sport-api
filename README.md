# containerized-sport-api
# Containerized Sports API

This repository contains a **containerized sports API** designed for providing real-time sports data through a RESTful interface. The project leverages modern development tools such as **Docker**, **Python**, and other libraries to create an efficient, scalable, and reusable application.

## Features
- **Real-time Sports Data:** Fetch live data about games, teams, and scores.
- **Containerized Deployment:** Simplifies running the application using Docker.
- **Extensibility:** Easily adaptable for additional APIs or sports.
- **RESTful API:** Provides structured responses for easy integration.

## Technologies Used
- **Python**: Backend development using Flask/FastAPI.
- **Docker**: For containerized application deployment.
- **API Integration**: Sports data is retrieved via external APIs like the NBA API.
- **Dependencies**:
  - `requests` for API calls.
  - `Flask` or `FastAPI` for REST API.
  - Additional libraries as defined in `requirements.txt`.

## Prerequisites
Before running the project, ensure you have the following installed:

- Docker ([Download Docker](https://www.docker.com/products/docker-desktop))
- Python 3.8 or later ([Download Python](https://www.python.org/downloads/))
- Git ([Download Git](https://git-scm.com/))

## Installation and Setup

1. **Clone the Repository**
   ```bash
   git clone https://github.com/ameh0429/containerized-sport-api.git
   cd containerized-sport-api
   ```

2. **Set Up Environment Variables**
   Create a `.env` file in the root directory and populate it with the required API keys and configurations:
   ```env
   API_KEY=<Your_Sports_API_Key>
   BASE_URL=<Sports_API_Base_URL>
   ```

3. **Build the Docker Image**
   Build the container using the provided `Dockerfile`:
   ```bash
   docker build -t containerized-sport-api .
   ```

4. **Run the Docker Container**
   Start the containerized application:
   ```bash
   docker run -d -p 5000:5000 --env-file .env containerized-sport-api
   ```

5. **Access the API**
   The API will be available at `http://localhost:5000`. Use an API client like Postman or cURL to interact with the endpoints.

## Endpoints
Here are some key endpoints provided by the API:

- **GET `/games`**: Retrieve a list of live games.
- **GET `/teams`**: Fetch details about teams.
- **GET `/scores`**: Get live scores for a specific game.

For detailed documentation, refer to the [API Documentation](docs/api-docs.md).

## Development Workflow

1. **Install Dependencies**
   If you wish to run the app locally (without Docker):
   ```bash
   pip install -r requirements.txt
   ```

2. **Run the Application**
   ```bash
   python app.py
   ```

3. **Testing**
   Run unit tests to ensure functionality:
   ```bash
   pytest tests/
   ```

## Contributing
Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch-name`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature-branch-name`).
5. Open a pull request.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments
- [NBA API](https://www.nba.com/stats) for live sports data.
- Docker and Python community for tools and libraries.

---

Feel free to raise issues or submit feature requests via the [Issues](https://github.com/ameh0429/containerized-sport-api/issues) tab.
