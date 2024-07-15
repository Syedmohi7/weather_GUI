# Jeelani Weather Gui

Jeelani Weather App is a simple weather application built using Python's Tkinter library for the GUI and the OpenWeatherMap API to fetch weather data.

## Features
- User-friendly interface.
- Fetches current weather information for Indian states and union territories.
- Displays weather condition, description, temperature in Celsius, and atmospheric pressure.

## Requirements
- Python 3.x
- Tkinter library (usually comes with Python installations)
- Requests library (`pip install requests`)

## Setup and Installation

1. **Clone the repository or download the source code:**

    ```bash
    git clone <repository_url>
    ```

2. **Navigate to the project directory:**

    ```bash
    cd JeelaniWeatherApp
    ```

3. **Install the required Python libraries:**

    ```bash
    pip install requests
    ```

## Usage

1. **Run the application:**

    ```bash
    python weather_app.py
    ```

2. **Interface Description:**
    - A dropdown menu to select a state or union territory in India.
    - Labels to display the weather condition, description, temperature, and pressure.
    - A "Done" button to fetch and display the weather data.

3. **Steps:**
    - Open the application.
    - Select a state or union territory from the dropdown list.
    - Click the "Done" button.
    - The application will fetch and display the current weather information for the selected location.

## Code Explanation

- **Imports:**
    ```python
    from tkinter import *
    from tkinter import ttk
    import requests
    ```

- **Function to Fetch Weather Data:**
    ```python
    def data_get():
        city = city_name.get()
        data = requests.get(
            "https://api.openweathermap.org/data/2.5/weather?q=" + city + "&appid=86b885377a88daacb0a8d890c8e7c3c8"
        ).json()
        w_lable1.config(text=data["weather"][0]["main"])
        wd_lable1.config(text=data["weather"][0]["description"])
        temp_lable1.config(text=str(int(data["main"]["temp"] - 273.15)))
        per_lable1.config(text=data["main"]["pressure"])
    ```

- **Tkinter GUI Setup:**
    ```python
    win = Tk()
    win.title("Jeelani Weather App")
    win.config(bg="light blue")
    win.geometry("500x600")

    name_lable = Label(win, text="Jeelani Weather App", font=("Time New Roman", 25, "bold"))
    name_lable.place(x=25, y=50, height=50, width=450)

    city_name = StringVar()
    list_name = ["Andhra Pradesh", "Arunachal Pradesh", "Assam", "Bihar", "Chhattisgarh", "Goa", "Gujarat", "Haryana", 
                 "Himachal Pradesh", "Jammu and Kashmir", "Jharkhand", "Karnataka", "Kerala", "Madhya Pradesh", 
                 "Maharashtra", "Manipur", "Meghalaya", "Mizoram", "Nagaland", "Odisha", "Punjab", "Rajasthan", 
                 "Sikkim", "Tamil Nadu", "Telangana", "Tripura", "Uttar Pradesh", "Uttarakhand", "West Bengal", 
                 "Andaman and Nicobar Islands", "Chandigarh", "Dadra and Nagar Haveli", "Daman and Diu", "Lakshadweep", 
                 "National Capital Territory of Delhi", "Puducherry"]

    com = ttk.Combobox(win, text="Select Location", values=list_name, font=("Time New Roman", 25, "bold"), textvariable=city_name)
    com.place(x=25, y=120, height=50, width=450)

    w_lable = Label(win, text="Weather Climate", font=("Time New Roman", 15))
    w_lable.place(x=25, y=260, height=50, width=200)

    w_lable1 = Label(win, text="", font=("Time New Roman", 15))
    w_lable1.place(x=250, y=260, height=50, width=200)

    wd_lable = Label(win, text="Weather Description", font=("Time New Roman", 15))
    wd_lable.place(x=25, y=330, height=50, width=200)

    wd_lable1 = Label(win, text="", font=("Time New Roman", 15))
    wd_lable1.place(x=250, y=330, height=50, width=200)

    temp_lable = Label(win, text="Temperature", font=("Time New Roman", 15))
    temp_lable.place(x=25, y=400, height=50, width=200)

    temp_lable1 = Label(win, text="", font=("Time New Roman", 15))
    temp_lable1.place(x=250, y=400, height=50, width=200)

    per_lable = Label(win, text="Pressure", font=("Time New Roman", 15))
    per_lable.place(x=25, y=470, height=50, width=200)

    per_lable1 = Label(win, text="", font=("Time New Roman", 15))
    per_lable1.place(x=250, y=470, height=50, width=200)

    done_button = Button(win, text="Done", font=("Time New Roman", 25, "bold"), command=data_get)
    done_button.place(y=190, height=50, width=100, x=200)

    win.mainloop()
    ```

## API Key

The current API key used in the code is `86b885377a88daacb0a8d890c8e7c3c8`. You may need to replace this with your own API key from OpenWeatherMap for personal use.

## Contributions

Contributions to the project are welcome. Please follow standard practices for submitting issues and pull requests.

## License

This project is licensed under the MIT License.

## Contact

For any inquiries or support, please contact Jeelani at [your_email@example.com].

---

Thank you for using Jeelani Weather App!