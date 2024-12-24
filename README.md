SchoolList Component - WizFit Challenge

Overview

The SchoolList component is a Vue.js application designed to integrate with the WizFit Challenge API. It provides a responsive, user-friendly interface to display participating schools and includes a dynamic search feature.

Features

Dynamic Search: Allows users to filter the list of schools in real time.

API Integration: Fetches data from the WizFit Challenge API.

Responsive Design: Ensures compatibility across devices.

Error Handling: Handles failed requests and empty results gracefully.

Getting Started

Prerequisites

Ensure you have the following installed:

Node.js

npm or Yarn

Installation

Clone the repository:

git clone <repository-url>

Navigate to the project directory:

cd school-list

Install dependencies:

npm install

Run the Application

To start the development server:

npm run serve

The application will be accessible at http://localhost:8080.

API Details

Endpoint:

https://api.devharlemwizardsinabox.com/campaign/campaign_school_list/?search=

Method: GET

Parameters:

search: (optional) Query string to filter school results.

Example Request

GET https://api.devharlemwizardsinabox.com/campaign/campaign_school_list/?search=example

File Structure

SchoolList.vue: Main component file.

assets/: Contains images and other static files.

style/: Contains scoped CSS for the component.

How It Works

Data Flow

The fetchSchools method fetches data from the WizFit API.

User input is bound to searchQuery via v-model, triggering the search dynamically.

The schools are displayed in a styled list with hover effects.

Error Handling

Errors during API calls are logged to the console.

If an error occurs, the school list is cleared, and no schools are displayed.

Styling

The application uses:

Responsive Design: Media queries ensure proper rendering on mobile and desktop devices.

Hover Effects: Enhance interactivity for buttons and cards.

Thematic Colors: Matches the WizFit Challenge branding.

Screenshots

Home Screen:
Displays the introductory banner and search box.

Search Results:
Shows the filtered list of schools.

No Results:
A message indicating no schools found for the search query.


Deployment

To deploy the application, build the production version:

npm run build




