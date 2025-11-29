from google.adk.agents import Agent
from zoneinfo import ZoneInfo
import datetime
import requests
def current_time(city: str):
    """Returns the current time in a specified city."""
    url = f"https://wttr.in/{city}?format=j1"
    try:
        data = requests.get(url).json()
        local_time = data['current_condition'][0]['localObsDateTime']
        return {"status": "success", "report": f"The current time in {city} is {local_time}."}
    except Exception as e:
        return {"status": "error", "report": f"Could not get time for {city}: {e}"}

def current_weather(city: str):
    """Returns the current weather in a specified city."""
    url = f"https://wttr.in/{city}?format=j1"
    data = requests.get(url).json()
    return data

root_agent = Agent(
    name="weather_time_agent",
    model="gemini-2.0-flash",
    description=(
        "Agent to answer questions about the time and weather in a city."
    ),
    instruction=(
        "You are a helpful agent who can answer user questions about the time and weather in a city."
    ),
    tools=[current_time, current_weather],
)
