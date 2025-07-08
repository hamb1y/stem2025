# STEM 2025 - Music & HRV Research Project

This project is a web-based application designed for a school STEM project. It conducts an experiment to analyze the relationship between music and human heart-rate variability (HRV). The application guides users through an interactive tour, playing various song snippets, collecting their feedback, and recording their physiological responses via an external heart rate sensor.

## ✨ Features

- **Interactive Experiment Flow:** A multi-page guided tour for a seamless user experience.
- **Music Playback:** Plays 6 different song snippets to the user.
- **Data Collection:** Gathers user information, subjective feelings, and opinions on the music.
- **HRV Monitoring:** Interfaces with an Arduino and a MAX30102 sensor to collect heart-rate variability data in the background.
- **Theming:** Includes a light/dark mode theme switcher.

## 💻 Tech Stack

- **Frontend:** [Astro.js](https://astro.build/)
- **Backend (Planned):** [Python (Flask)](https://flask.palletsprojects.com/)
- **Hardware:**
  - Arduino Nano (CH340)
  - MAX30102 Pulse Oximeter and Heart-Rate Sensor

## 🚀 Project Setup & Usage

To run this project locally, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd stem2025
    ```

2.  **Install dependencies:**
    This project uses [pnpm](https://pnpm.io/) as the package manager.
    ```bash
    pnpm install
    ```

3.  **Run the development server:**
    ```bash
    pnpm dev
    ```
    This will start the development server, typically at `http://localhost:4321`.

4.  **Build for production:**
    ```bash
    pnpm build
    ```

5.  **Preview the production build:**
    ```bash
    pnpm preview
    ```

## 🔬 Hardware Setup

The application is designed to work with an Arduino Nano connected to a MAX30102 heart rate sensor to collect HRV data.

-   **Connection:**
    -   **MAX30102 VCC** -> **Arduino 5V**
    -   **MAX30102 GND** -> **Arduino GND**
    -   **MAX30102 SDA** -> **Arduino A4** (I2C Data)
    -   **MAX30102 SCL** -> **Arduino A5** (I2C Clock)
-   **Arduino Code:** The Arduino must be programmed with a sketch that reads data from the sensor and sends it over the serial port. See `GEMINI.md` for a code example and library recommendations.

## 📊 Data Structure

The application collects all experiment data into a single JSON object per user "tour". The backend will be responsible for receiving and storing these objects.

```json
{
  "DATE": "<T:{UNIXTIME}>",
  "USER INFO": {
    "USER NAME": "{USER PROVIDED STRING}",
    "USER AGE": "{USER PROVIDED INTEGER}",
    "USER DEMOGRAPHIC": "{STRING SET BASED ON USER AGE}"
  },
  "TRACKS": {
    "1": {
      "SONG_NAME": "...",
      "SONG_ID": "...",
      "USER_AVERAGE_HRV": "...",
      "USER_OPINION": "...",
      "USER_FEELING": "...",
      "SONG_TEMPO": "...",
      "SONG_GENRE": "...",
      "SONG_DEMOGRAPHIC": "..."
    },
    "2": { "..."},
    "3": { "..."},
    "4": { "..."},
    "5": { "..."},
    "6": { "..."}
  }
}
```