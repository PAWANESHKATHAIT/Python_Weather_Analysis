# Weather Analysis & Report Generation Tool (Jupyter Notebook Version)

## Objective
This project provides a Python-based tool for fetching current weather data for a list of cities. It saves this data, performs basic analysis, generates a formatted report, and can optionally visualize temperature data through a plot, all designed to be run within a Jupyter Notebook environment.

## Your Approach

1.  **Jupyter Notebook Integration:** The entire logic is designed to be executed cell-by-cell within a Jupyter Notebook, making it interactive and easy to inspect intermediate results.
2.  **API Integration:** It uses the **OpenWeatherMap API** to gather real-time weather information (temperature, humidity, weather description, wind speed). Robust error handling is implemented to manage issues like invalid API keys, cities not found, or network problems gracefully.
3.  **Data Persistence:** Collected weather data is stored in a structured **JSON file** (`weather_data.json`) for easy access and re-analysis without needing to re-fetch from the API every time.
4.  **Data Analysis:** The tool analyzes the fetched data to provide key insights, such as identifying cities with the highest/lowest temperatures, calculating the average temperature, and listing cities with "clear sky" or "rain" conditions.
5.  **Report Generation:** A comprehensive and easy-to-read **text report** (`summary_report.txt`) is automatically generated, summarizing all the analysis results.
6.  **Optional Plotting:** For visual insight, the tool can generate a **bar chart of temperatures** across all processed cities, saved as a PNG image (`temperature_chart.png`).

## How to Run the Code

### Prerequisites

* **Python 3.8+**: Ensure you have a compatible Python version installed.
* **Jupyter Notebook**: You'll need Jupyter Notebook installed. If not, you can install it via pip: `pip install notebook`.
* **OpenWeatherMap API Key**: You'll need a free API key from OpenWeatherMap. Sign up and get yours from [https://openweathermap.org/api](https://openweathermap.org/api).
* **Internet Connectivity**: An active internet connection is required to fetch weather data.

### Setup Steps

1.  **Save the Notebook Content**:
    * Create a new Jupyter Notebook (e.g., `weather_analysis.ipynb`).
    * Copy the provided code into separate cells in your notebook as indicated by the `# --- Cell X: ... ---` comments.
2.  **Configure API Key**:
    * In **Cell 1** of your Jupyter Notebook, replace `"YOUR_OPENWEATHERMAP_API_KEY"` with your actual OpenWeatherMap API key.
3.  **Install Dependencies**: Open a cell in your Jupyter Notebook and run the following command to install the required libraries:
    ```python
    !pip install requests matplotlib
    ```
    (The `!` allows you to run shell commands from within Jupyter.)
4.  **Create `my_cities.txt`**: **Cell 8** of the notebook code includes a block that automatically creates `my_cities.txt` with sample cities. Make sure to run this cell before executing the `run_weather_analysis` function. You can modify this block to include your desired list of cities.

### Execution

1.  **Open Jupyter Notebook**: Start Jupyter from your terminal in the directory where you saved your `.ipynb` file:
    ```bash
    jupyter notebook
    ```
2.  **Run Cells**: Open your `weather_analysis.ipynb` file. Execute each cell sequentially from Cell 1 to Cell 8.
3.  **Execute Analysis**: In **Cell 8**, uncomment and run the specific `run_weather_analysis()` function call that fits your needs. The provided example already calls it with `cities_file="my_cities.txt"` and `plot_flag=True`.

    **Example Calls you can use in Cell 8:**
    ```python
    # Run with default settings (reads cities.txt if it exists, otherwise my_cities.txt if Cell 8 creates it first)
    # run_weather_analysis()

    # Run and generate a plot using my_cities.txt
    run_weather_analysis(cities_file="my_cities.txt", plot_flag=True)

    # Run with custom output file names
    # run_weather_analysis(cities_file="my_cities.txt", output_data_file="custom_data.json", report_file="custom_report.txt")
    ```

## Expected Output

After successful execution, the following files will be generated in the same directory as your Jupyter Notebook:

* **`my_cities.txt`**: The input file containing the list of cities.
* **`weather_data.json`**: A JSON file containing the raw weather data fetched from the API for each city.
* **`summary_report.txt`**: A plain text file summarizing the weather analysis insights.
* **`temperature_chart.png`**: An image file displaying a bar chart of temperatures (if `plot_flag=True`).

## Any Assumptions Made

* **Valid OpenWeatherMap API Key**: A correctly configured and valid API key is essential for fetching data.
* **City Name Accuracy**: It's assumed that the city names provided in the input file are reasonably accurate and can be recognized by the OpenWeatherMap API. The tool includes error handling for cities not found.
* **Internet Connectivity**: The tool relies on an active internet connection for all API calls.
* **API Rate Limits**: Usage is expected to stay within OpenWeatherMap's free tier API call limits.
* **Python Environment**: Assumes a standard Python environment where necessary libraries can be installed via `pip`.
