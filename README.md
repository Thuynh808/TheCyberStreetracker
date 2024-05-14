![cyberstreetracker](https://i.imgur.com/EvXE8lo.png)

## Introduction

Welcome to **The Cyber Streetracker**, a comprehensive web application designed to centralize and streamline access to cybersecurity news and tools. This project was developed with two primary objectives:

- **Preparation for the AZ-500 Certification**:
   - To deepen my understanding of Azure security services and apply best practices in a practical context.

- **Exploration of Threat Intelligence and SOC Analyst Tasks**:
  - To build a tool that aggregates real-time data from sources like The Hacker News RSS feed and the National Vulnerability Database (NVD), providing valuable insights for monitoring and responding to emerging threats.

**The Cyber Streetracker** features:
- **User Authentication via OAuth 2.0**: Secure access through OAuth 2.0 and OpenID Connect.
- **Real-Time News Updates**: Integration with The Hacker News RSS feed for the latest cybersecurity incidents.
- **NVD CVE Search**: A dedicated tool for searching the National Vulnerability Database for detailed information on specific vulnerabilities.
- **User Experience Enhancements**: Intuitive navigation, session management, and quick access to key features.

This project is designed to empower cybersecurity professionals and enthusiasts by providing timely information and tools necessary for staying informed and proactive in the cybersecurity landscape.
<br><br><br>

![cyberstreetracker1](https://i.imgur.com/pMcGUym.png)

## Architecture Overview

The architecture of **The Cyber Streetracker** is designed to ensure robust functionality and security. The above diagram illustrates the overall architecture:

- **Frontend**:
  - **Azure Static Web App**: Hosts the frontend application.
  - **HTML, CSS, JavaScript**: Core technologies for building the user interface.
- **Backend**:
  - **Azure Function App**: Manages backend logic and API integrations.
- **Security and Access**:
  - **OAuth 2.0 Auth Code Flow**: Handles user authentication.
  - **Entra ID**: Manages identity and access.
- **Data Sources**:
  - **Hacker News RSS Feed**: Provides real-time news updates.
  - **National Vulnerability Database (NVD)**: Supplies CVE information.
- **DevOps**:
  - **GitHub Actions**: Facilitates continuous integration and deployment (CI/CD).
- **Network and Security**:
  - **Azure Front Door**: Ensures high availability and secure access.
  - **Web Application Firewall (WAF)**: Protects against common web exploits.
- **Monitoring and Management**:
  - **Azure Monitor**: Tracks performance and health.
  - **Log Analytics Workspace**: Aggregates and analyzes logs.
  - **Defender for Cloud**: Enhances security posture.

This detailed architecture ensures a scalable, secure, and efficient solution for delivering critical cybersecurity information and tools.
<br><br>

<details>
<summary><h2><b>Section 1: Local Setup with GitHub</b></h2></summary>

![cyberstreetracker2](https://i.imgur.com/aBbgdD2.png)

This section describes the initial steps for setting up **The Cyber Streetracker** project locally. It covers cloning the repository, setting up the development environment in Visual Studio Code (VSCode), and organizing the project structure to facilitate efficient development and version control.

### Setup:

- **Clone the Repository**: Use SSH for secure access.
- **Open in VSCode**: Initialize the project in Visual Studio Code.
- **Create Directories**: Set up `frontend` for the user interface and `backend` for Azure Function App.
- **Version Control**: Use `git add`, `git commit`, and `git push` to manage changes.

### Key Points:

- **GitHub Cloning via SSH**: Ensures secure and efficient repository access.
- **VSCode Integration**: Supports both frontend and backend development.
- **Directory Structure**: Organized into `frontend` and `backend` for efficient code management.
- **Version Control**: Tracks and integrates changes using Git commands.

### Repository Structure

- **frontend**: Contains HTML, CSS, and JavaScript files.
- **backend**: Contains Azure Function App files.

With the local setup complete, our integration with GitHub streamlines version control, facilitates collaboration, and supports continuous integration. This setup ensures efficient project contributions and high-quality code maintenance. Next, we will focus on developing and enhancing the frontend components of our web app.
<br><br><br>

---
</details>

<details>
<summary><h2><b>Section 2: Frontend Development</b></h2></summary>

![cyberstreetracker3](https://i.imgur.com/sMkck0h.png)

The frontend of **The Cyber Streetracker** is structured to provide a user-friendly interface that integrates seamlessly with the backend services. The project uses a Bootstrap HTML5 template as the framework for the frontend build, ensuring a responsive and visually appealing design.

### Frontend Codebase Structure

- **HTML**: Forms the structure of the web pages, providing the essential elements and containing the core layout and Bootstrap framework integration
- **CSS**: Styles the HTML elements, enhancing the visual presentation and user experience
- **JavaScript**: Adds interactivity and handles dynamic content updates like managing user interactions and API calls

### Interaction Flow

- **Landing Page**:
   - Users are greeted with a welcome message and a login button if not authenticated.
   - Upon successful login via OAuth 2.0, users gain access to additional features.

- **News Feed Section**:
   - Dynamically loads the latest cybersecurity news articles using JavaScript to fetch data from The Hacker News RSS feed.

- **CVE Search Tool**:
   - Allows users to search for specific CVEs, displaying detailed vulnerability information retrieved from the NVD API.

### Extensions Used in VSCode

To facilitate development, several VSCode extensions are recommended:
- **Live Server**: Provides a local development server with live reload.
- **Azure Account**: Integrates Azure services within VSCode.
- **Azure Tools**: Includes a suite of tools for managing Azure resources.
- **Azure Functions**: Supports development and debugging of Azure Functions.
- **Python**: Essential for any Python-related backend tasks.
- **GitHub Actions**: Assists in managing CI/CD workflows.

We have established a solid foundation for the frontend of **The Cyber Streetracker**, utilizing a Bootstrap HTML5 template to create a responsive and user-friendly interface. The structure includes HTML for page layout, CSS for styling, and JavaScript for dynamic content and API integration. We have set up essential sections such as the landing page, news feed, and CVE search tool, ensuring a seamless user experience. Although we have laid the groundwork, we will revisit the frontend later to integrate secure sign-in features and refine the interface further. For now, our focus shifts to building the core backend functions to support these frontend capabilities.
<br><br><br>

---
</details>


<details>
<summary><h2><b>Section 3: Backend Development</b></h2></summary>

![cyberstreetracker4](https://i.imgur.com/G8PTj6B.png)

The backend of **The Cyber Streetracker** was developed using Python and Flask, providing a robust framework for handling API calls and integrating external data sources.

### Backend Codebase Structure

- **Flask**: Serves as the web framework for handling HTTP requests and routing.
- **Python Modules**: Utilized to enhance functionality and simplify development.
  - **Flask-Caching**: Implements caching mechanisms to improve performance.
  - **Flask-CORS**: Enables Cross-Origin Resource Sharing (CORS) to allow resource sharing across different domains.
  - **Requests**: Simplifies HTTP requests to external APIs.
  - **Feedparser**: Parses RSS feeds to retrieve news articles.
  - **Bleach**: Sanitizes HTML content to prevent security vulnerabilities.
  - **re**: Provides regular expression operations for string matching.
  - **Datetime**: Manages date and time operations.

### API Integrations

- **RSS Feed API**:
  - **Purpose**: Fetches and processes news articles from The Hacker News RSS feed.
  - **Functionality**: Uses `feedparser` to parse feed data and `bleach` to sanitize HTML content, providing a secure and structured output of the latest articles.

- **CVE Search API**:
  - **Purpose**: Interfaces with the National Vulnerability Database (NVD) to search for Common Vulnerabilities and Exposures (CVEs).
  - **Functionality**: Utilizes `requests` to fetch data from the NVD API, processes query parameters, and returns detailed CVE information, including descriptions, CVSS scores, and severity.

### Interaction Flow

- **Data Retrieval**:
   - **RSS Feed Function**: Fetches and processes news data from The Hacker News.
   - **CVE Search Function**: Retrieves and processes CVE data from the NVD.

- **API Endpoints**:
   - **/rss-feed**: Returns the latest news articles.
   - **/cve/<cve_id>**: Returns detailed CVE information based on user queries.

These functions were tested locally and confirmed that the JSON responses were correctly integrated into the HTML, ensuring the application displays real-time cybersecurity news and CVE details effectively.
<br><br><br>

---
</details>

<details>
<summary><h2><b>Section 4: OAuth2 Authentication and Authorization</b></h2></summary>

![cyberstreetracker5](https://i.imgur.com/IyM2Aze.png)

The **OAuth2 Authentication and Authorization** for **The Cyber Streetracker** is designed to provide secure user access, leveraging Microsoft's Entra ID platform and the MSAL (Microsoft Authentication Library) in the frontend.

### Azure App Registration

- **Setup**:
  - **Application Registration**: Configured in Azure to define and manage the web app's identity.
  - **Redirect URI Configuration**: Specified the URI where the authorization server sends the user once the app has been successfully authorized, crucial for receiving tokens and completing the authentication process.
  - **Avoiding Implicit Grant Flow**: Ensured the app uses Authorization Code Flow with PKCE for enhanced security.

- **Demo User and Group**:
  - **Creation**: A demo user was created and placed in a demo group.
  - **Group Assignment**: The demo group was added to the app registration’s identity settings in Entra ID, allowing controlled access to the web app.

### Authentication Flow

- **Opens Browser**: The user initiates the process by opening their browser.
- **Navigates to App**: They navigate to the web app, which triggers the authentication flow.
- **Redirect to Entra ID**: The web app redirects the user to Entra ID (Azure AD) with an authorization code request and code challenge.
- **Enters Credentials**: The user enters their credentials on the Entra ID login page.
- **Receives Authorization Code**: Upon successful login, Entra ID issues an authorization code.
- **Request Bearer Token**: The web app exchanges the authorization code for a bearer token, providing the code verifier and authorization code.
- **Issue Tokens**: Entra ID issues the tokens, which include access and ID tokens.
- **Redirect Access Tokens**: The tokens are redirected back to the web app via the specified redirect URI.
- **Returns Secure Page**: The web app uses the access token to provide secure access to the user.

### Frontend Integration

- **MSAL Integration**:
  - **JavaScript**: MSAL.js is used in the frontend to handle OAuth2 flows, managing token acquisition and renewal.
  - **HTML**: Integration points in the HTML code facilitate secure sign-in and access token retrieval.

### Security Features

- **Bearer Token**:
  - **Purpose**: Used for authenticating API requests, ensuring secure communication between the frontend and backend.
  - **Handling**: The bearer token is securely stored and managed by MSAL.js.

- **Code Verifier and Challenge**:
  - **Purpose**: Enhances security by mitigating authorization code interception attacks.
  - **Process**: The code verifier is generated by the frontend and hashed to create a code challenge, sent with the authorization request.

### Benefits

- **Enhanced Security**: OAuth2 with PKCE (Proof Key for Code Exchange) ensures robust security.
- **Streamlined User Experience**: Seamless sign-in flow integrated with Microsoft Entra ID.
- **Scalable Authentication**: Supports secure authentication for multiple users and sessions.

The implementation of OAuth2 with MSAL, coupled with a robust app registration setup in Azure, provides **The Cyber Streetracker** with a secure and scalable authentication mechanism. This ensures user data and interactions remain protected, supporting our goal of delivering a secure and user-friendly application.
<br><br><br>

---
</details>

<details>
<summary><h2><b>Section 5: Deployment</b></h2></summary>

![cyberstreetracker6](https://i.imgur.com/fgXKzL7.png)

The deployment phase of **The Cyber Streetracker** focuses on setting up both backend and frontend components in Azure. This involves converting and deploying Python Flask functions to Azure Functions, creating a Static Web App for the frontend, and ensuring seamless integration and secure communication between them.

### Backend Deployment

- **Azure Login and Function App Creation**:
   - **VSCode Integration**: Logged in to Azure directly from Visual Studio Code.
   - **Create Function App**: Used the Azure extension in VSCode to create a new Function App in Azure.

- **Convert Python Flask Functions**:
   - **Blueprint Module**: Utilized the blueprint module to integrate the CVE search function and RSS feed function within Azure Functions.
   - **Update Function Code**: Adjusted Flask functions to fit Azure Function’s requirements, including setting up HTTP triggers and appropriate routing.
   - **API Configuration**: Configured the app registration in Azure to expose APIs, allowing secure access and integration.

- **Deployment Steps**:
   - **Deploy to Azure**: Published the converted Flask functions to the newly created Azure Function App.
   - **API Permissions**: Set up API permissions to allow the Function App to be accessed securely by the frontend.
   - **Configure App Settings**: Ensured all necessary environment variables and connection strings were configured in the Function App settings.

### Frontend Deployment

- **Create Static Web App**:
   - **VSCode Integration**: Used the Azure extension in VSCode to create an Azure Static Web App.
   - **Deploy Frontend**: Deployed the frontend code to the Azure Static Web App.

- **Integrate with Backend**:
   - **JavaScript Updates**: Modified JavaScript code to interface with the deployed Azure Function App.
   - **API Permissions**: Configured the web app to use delegated permissions for making calls to the Function App.

- **Testing and Validation**:
   - **Functionality Check**: Ensured all features, including CVE search and RSS feed, were functioning correctly.
   - **Cross-Origin Resource Sharing (CORS)**: Configured CORS settings to allow the frontend to communicate with the backend securely.
   - **Performance Testing**: Conducted basic performance tests to ensure the app runs smoothly under expected load conditions.
   - **Security Testing**: Verified that all security measures, including token handling and API permissions, were correctly implemented.

- **Update GitHub Repository**:
   - **Push Changes**: Pushed the updated code to GitHub to reflect the latest changes and deployment configurations.

The deployment process for **The Cyber Streetracker** involved converting Python Flask functions to Azure Functions, creating a Static Web App for the frontend, and ensuring seamless integration between the two. By configuring app registration, API permissions, and CORS settings, the communication channels between the frontend and backend were secured. After thorough testing, including functionality, performance, and security checks, the updated code was pushed to GitHub, maintaining an up-to-date repository and supporting continuous integration and delivery.
<br><br><br>

---
</details>

<details>
<summary><h2><b>Section 6: Continuous Integration and Deployment (CI/CD)</b></h2></summary>

![cyberstreetracker7](https://i.imgur.com/yR86aE0.png)

This section outlines the setup of Continuous Integration and Deployment (CI/CD) for **The Cyber Streetracker**, focusing on automating the deployment process using GitHub Actions. This setup ensures that changes to the code are automatically built and deployed, maintaining the efficiency and consistency of the web app.

### CI/CD Setup for Web App

- **GitHub Actions Configuration**:
   - **Workflow File**: Created a `.github/workflows` directory in the repository and added a workflow YAML file to define the CI/CD pipeline.
   - **Define Jobs**: Specified jobs in the workflow file to build and deploy the web app.

- **Automated Deployment**:
   - **Commit and Push**: Changes made in VSCode are committed to the GitHub repository.
   - **Trigger CI/CD Pipeline**: GitHub Actions is configured to automatically trigger the CI/CD pipeline upon code push or pull request.

- **Build and Deploy**:
   - **Build Job**: Configured to build the static web app using appropriate build tools and commands.
   - **Deploy Job**: Set up to deploy the built web app to Azure Static Web Apps.
   - **Azure Integration**: Utilized Azure credentials stored in GitHub Secrets for secure deployment.

### Benefits of CI/CD

- **Consistent Deployment**: Streamlines the deployment process, reducing manual errors.
- **Faster Releases**: Speeds up the release cycle by automating the build and deployment processes.
- **Continuous Feedback**: Provides immediate feedback on code changes, improving development efficiency.

The CI/CD setup for **The Cyber Streetracker** ensures that any changes made to the code are automatically deployed, maintaining the integrity and performance of the web app. By leveraging GitHub Actions, we have streamlined the development workflow, enabling continuous integration and delivery, and ensuring that the latest updates are always deployed efficiently to Azure Static Web Apps.
<br><br><br>

---
</details>

<details>
<summary><h2><b>Section 7: Azure Front Door and Web Application Firewall (WAF)</b></h2></summary>

![cyberstreetracker8](https://i.imgur.com/TmT1jTA.png)

This section describes the configuration of Azure Front Door and Web Application Firewall (WAF) for **The Cyber Streetracker**. These services enhance security and performance by providing load balancing, global distribution, and protection against common web exploits.

### Configuration Steps

- **Azure Front Door Setup**:
   - **Custom Domain and HTTPS**: Configured a custom domain with HTTPS to secure web traffic.
   - **Global Distribution**: Leveraged Azure Front Door’s capabilities to distribute traffic globally, improving access speed and reliability.
   - **Content Delivery Network (CDN)**: Integrated within Azure Front Door to cache static content, reducing latency and enhancing user experience.
   - **Origin Groups**: Configured two origin groups:
     - **Frontend**: Origin for the Azure Static Web App.
     - **Backend**: Origin for the Azure Function App.
   - **Routing Configuration**: Set up routes to direct traffic appropriately to the frontend and backend origins.

- **Web Application Firewall (WAF) Policy**:
   - **Custom Rules**: Defined custom rules, including a “US Only” rule to block IPs outside the US.
   - **OWASP Rule Set**: Implemented the OWASP Core Rule Set to protect against common vulnerabilities like SQL injection and cross-site scripting (XSS).

### Benefits of Front Door and WAF

- **Enhanced Security**: Protects the application from common web attacks and exploits.
- **Improved Performance**: Reduces latency and improves load times through global distribution and CDN integration.
- **Scalability and Reliability**: Ensures the application can handle traffic spikes and provides high availability.

The integration of Azure Front Door and WAF with **The Cyber Streetracker** enhances the overall security and performance of the application. By leveraging these services, the web app benefits from robust protection against threats and improved user experience through efficient content delivery.
<br><br><br>

---
</details>

<details>
<summary><h2><b>Section 8: Monitoring and Logging</b></h2></summary>

![cyberstreetracker9](https://i.imgur.com/1AwcEQL.png)

This section outlines the setup of monitoring and logging for **The Cyber Streetracker**, focusing on how Azure services such as Azure Monitor, App Insights, and Log Analytics are utilized to track application performance and security, along with monitoring sign-in activities through EntraID.

### Configuration of Monitoring and Logging Tools

- **Azure Monitor and App Insights**:
   - **Integration**: Connected the Azure Function App with Azure Monitor and Application Insights to track performance metrics and operational data.
   - **Insights**: Configured to collect detailed information about the application's operations, helping to diagnose errors and improve performance.

- **Log Analytics Workspace**:
   - **Setup**: Created a Log Analytics workspace to aggregate logs from various Azure services.
   - **Logs Collection**: Configured to collect diagnostic logs, activity logs from the Azure Function App, Azure Front Door, Web Application Firewall, and Entra ID.

- **Defender for Cloud**:
  - **Security Score and Recommendations**: Defender for Cloud provides a security score and tailored recommendations, helping to enhance the security posture by identifying potential vulnerabilities and guiding the implementation of best practices.
  - **Security Monitoring**: Enabled Azure Defender for Cloud to monitor security across Azure services, providing advanced threat protection and detection capabilities.


### Benefits of Effective Monitoring and Logging

- **Enhanced Security**: Provides real-time security monitoring and alerts to detect and respond to potential threats quickly, including unauthorized access attempts evident from sign-in logs.
- **Operational Efficiency**: Helps in identifying performance bottlenecks and operational issues, facilitating quick resolution and uptime.
- **Compliance and Auditing**: Supports compliance and auditing requirements by retaining detailed logs of all system and user activities, including authentication events.

The monitoring and logging framework established for **The Cyber Streetracker** ensures comprehensive visibility into the application's health, security, and user authentication activities. By leveraging Azure Monitor, App Insights, and Log Analytics, along with Entra ID sign-in logs, we maintain high operational standards and security, supporting proactive management and continuous improvement of the system.
<br><br><br>

---
</details>

<details>
<summary><h2><b>Reflections</b></h2></summary>

Throughout the development of **The Cyber Streetracker**, numerous challenges were encountered, strategic changes implemented, and valuable lessons learned. This project not only enhanced my technical skills but also deepened my understanding of both the complexities and the critical aspects of building a secure and efficient web application.

#### Challenges Overcome
- **Integrating Multiple Azure Services**: Learning to seamlessly integrate various Azure services such as Azure Functions, Azure Static Web Apps, and Azure AD was initially daunting. Ensuring these services worked together effectively involved a steep learning curve.
- **Authentication Flows**: Implementing OAuth2.0 and managing authentication tokens securely, particularly handling the complexities around secure token storage and renewal, was challenging and required careful consideration to ensure security best practices.
- **Custom Domain Configuration**: Initially, I faced issues with too many redirect errors when setting up a custom domain with Azure Front Door after configuring it initially with the static web app. The solution was to remove the custom domain configuration from the static web app and reconfigure it directly through Azure Front Door.
- **Responsive Design for Mobile View**: Adjusting the frontend tables to render correctly in mobile view was a challenge. I learned to effectively use Bootstrap and CSS to make the UI responsive and user-friendly on various devices.
- **Converting Flask App to Azure Functions**: Adapting the Flask application to work within the constraints of Azure Functions was complex. Discovering and implementing Blueprints greatly simplified the process, making the function modular and easier to manage.
- **Frontend and Backend Synchronization**: Enhancements to the interaction between the frontend and backend were made to improve data flow and user experience, ensuring that the frontend dynamically reflected changes from the backend in real-time.
- **Security First**: The importance of security in every aspect of the application became evident, particularly in protecting API endpoints, securing user authentication, and safeguarding sensitive data.

#### Security Testing
- **WAF Rule Testing**: Tested login attempts from outside the US using a VPN to verify the effectiveness of the WAF rules. The attempt was immediately blocked, confirming the functionality of the "US Only" rule.

![cyberstreetracker11](https://i.imgur.com/90JQHoM.png)
<br><br>
![cyberstreetracker12](https://i.imgur.com/ZU7WkwQ.png)
<br><br>

- **Least Privilege Testing**: Configured a demo user as a guest with minimal privileges and tested access to Entra ID's user directory, which was correctly blocked.

![Access Denied](https://i.imgur.com/0iuNuQK.png)
<br><br>

#### Enjoyable Aspects
- **Building with Azure**: Working with Azure's cloud infrastructure was immensely satisfying. It offered robust solutions and a broad range of services that enhanced the application's functionality and security.
- **User Interface Design**: Developing a user-friendly and aesthetically pleasing interface was particularly rewarding. It improved user engagement and made the application more intuitive.
- **Python Coding Success**: The moment when my Python code returned the exact response I wanted was a milestone, signifying that the backend was correctly processing and delivering data as expected.
- **OAuth2 Implementation**: Successfully implementing the OAuth2 authorization code flow with a code verifier and bearer token was a breakthrough, providing robust security for user authentication.

#### Conclusion
The **Cyber Streetracker** project was not just a technical journey but a significant personal growth opportunity. It solidified my career transition into cybersecurity and contributed immensely to passing the AZ-500 certification. This project has laid a strong foundation for future enhancements. Plans to integrate CosmosDB for user CVE search history and to use this web application as a platform for learning more about application security, exploring OWASP standards, and utilizing tools like Burp Suite are already underway. This is just the beginning, and I look forward to continuing to develop and refine **The Cyber Streetracker**.

</details>


