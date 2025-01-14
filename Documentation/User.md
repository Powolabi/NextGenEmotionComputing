# Unity application

## Note for running the application the first time

---

By default users have to approve any application requesting data from the HP Omnicept for data collection. Normally a toast message will appear on Windows asking for approval, but if it doesn't or you have toast messages turned off you can open the **HP Omnicept Tray App** and approve the application as shown below.

![HP Omnicept Tray app approval](./images/OmniceptTrayApp.png)

## Features

---

The primary use for this application is to display the data being collected from the HP Omnicept sensors while using the headset.

### Eye tracking and pupilometry

- On the side of the window there are two panels to display the data for the eye tracking and pupilometry sensors.
- The top window will display the pupil dialation of each eye in millimeters and through a dot in that will change it's size depending on the user's dialation.
- The bottom panel will display the combined gaze (roughly where a user is looking) in the form of a three-dimensional coordinate.

<img src="./images/Iteration3Pupil.png" alt="Eye tracking and pupilometry panels" width=250px>

### Heart Rate

- In the center of the window is the smallest panel that displays the heart rate of the user (beats per minute).
- The heart in the center will also pulse and change color depending on the user's heart rate.
- If the user's heart rate is less than 75 the heart will pulse slow with a light blue color. If between 76 and 135, the heart will pulse a bit faster with a yellow color. If between 136 and 175, the heart will beat faster and with a light red color. Finally, if the user's heart rate is above 176, the heart will pulse faster than before and with a dark red color.


<img src="./images/Iteration3Hr.png" alt="Heart Rate Panel" width=250px>

### Cognitive load

- On the right of window there is a panel that displays the cognitive load of a user in a range from 0.0 to 1.0.
- The circle around the load number is a bar that will fill and change color depending on what the user's congitive load is.
- If the user's cognitive load is less than 0.40, the bar would fill to the load with a light blue color. If the load is between 0.41 and 0.66, the bar would fill to the load with a yellow color. If the user's load is between 0.67 and 0.75 the bar would fill with a light red color. Finally, if the user's cognitive load is greater than 0.76, the bar would fill to the load point with a dark red color.
- Cognitive load is a scientific tearm for a measurement of mental effort required to perform a task. Here is a [link](https://www.youtube.com/watch?v=2Sk2_4U58yg) to a video from HP explaining cognitive load in more detail.

<img src="./images/Iteration3CognitiveLoad.png" alt="Cognitive load panel" width=250px>

### Ending a session

### Saving Data

- After ending the session, the application will display options to add a note to the session, **Upload Session Data**, and **Save Session Data to Disk**.
- Notes may be added by typing text into the provided text field and clicking the **Add Note** button.
- When you press the **Save Session Data to Disk** button the user's data will ben saved to a folder on the local device. After the data has been saved, the file location will be displayed and a button will appear to automatically copy the location to the clipboard.
- When you press the **Upload Session Data** button the user's data will then be uploaded to an AWS S3 bucket that stores the data by UserID and by timestamp of when uploaded.

<img src="./images/Iteration3SaveData.png" alt="Save Data" width=275px>

#### Mouth camera recording

- Video from the integrated mouth camera is recorded automatically when a session is started and stopped when the session is ended. No preview of the collected video is displayed.
- Recordings are saved alongside their associated session data on the local device. Note that recordings are saved locally _even if the *Save Session Data to Disk* button is not pressed!_
- As of the time of writing, video data is not uploaded to any form of cloud storage, even if the **Upload Session Data** button is pressed.


# Web application

## Login

Users can access their datasets by entering the email and password they created during registration.

![Login Screen](./images/WebLogin.png)

To get to registration click the link under the "LOGIN" button and create an account using your email on this page.

![Registration Screen](./images/WebRegister.png)

## Features

---

### Select Dataset

- The Simulation Results will appear on your dashboard. You can select which simulation's dataset to view.

![Dropdown](./images/WebDropdown.png)

![Dropdown with Options](./images/WebDropdown2.png)

### Chart Details

- You can see the value of specific points on the chart by hovering over them.

![Hover Details](./images/WebHover.png)

### Filter Charts

- You can filter which charts they want to view by clicking the pill toggles.

![Heart Rate Shown](./images/WebFilter.png)

![Heart Rate Hidden](./images/WebFilter2.png)

### Add Dataset Notes

- To add a note to a session dataset, click on any of the charts. A window will appear with the data and timestamp values automatically filled in, and more space to add a note.

![Note Taker UI](./images/FloatingNoteTaker.png)

### View Dataset Notes
- To view all saved notes for a given dataset, click "View Session Notes".
![View Session Notes Button](./images/WebShowSessionNotesButton.png)
![Session Notes UI](./images/NoteViewer.png)

### Export PDF

- You can export the data to a PDF by clicking "Export PDF".

![PDF Export](./images/WebExportPDF.png)

![PDF Export Results](./images/WebExportPDFResult.png)

### Export Raw Data

- You can export the data to a JSON by clicking "Export Raw Data".

![PDF Export](./images/WebExportData.png)

![PDF Export Results](./images/WebExportDataResult.png)

### Admin Page

- On the admin page, the user can perform executive functions such as creating and deleting organizations/users.

![Admin Portal](./images/AdminDashboard.png)
![Admin Portal User Manager](./images/UserManager.png)
![Admin Portal User Creator](./images/UserCreator.png)

### Manager Page

- The manager page allows someone from the organization that is acting as a manager to access all the user's data that is in that organization. The manager can see a list of all users in the same organization, they can then click on the link and be taken to the individual's datasets to be reviewed.

![Manager Portal](./images/ManagerPortal.png)