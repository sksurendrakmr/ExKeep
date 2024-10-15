# ExKeep
A react-native app to keep track of personal daily expenses and view the expenses summary


Presently, there exists a process in need of optimization for store employees to report operational issues encountered during tasks such as credit applications, profile creation, and conversion to pro memberships. The existing workflow requires employees to report issues to store managers, who then navigate various channels to relay the problem to the appropriate product teams. As a consequence, there is a delay of approximately 3-4 days in communicating the issue to the relevant domain team, followed by an additional 5-6 days to ascertain the root cause.

Upon reaching the appropriate domain team, essential details such as the occurrence date, user email, and operational flow are regrettably absent, thereby impeding swift resolution by developers.

To address this challenge, it is imperative to establish a streamlined system that enables real-time reporting of bugs by store employees with comprehensive information. This system should facilitate direct notification to the domain team upon issue reporting, thereby expediting the identification and resolution process.


In conclusion, enhancing the current system's effectiveness in reporting operational issues is imperative for improving customer satisfaction and organizational productivity. Implementing a streamlined reporting mechanism facilitates real-time communication between store employees and domain teams, saving valuable time and ensuring issues are reported with all required information for quick root cause analysis. This investment in bridging the gap between store employees and domain teams is essential for maintaining competitiveness and meeting stakeholder needs. Prioritizing the establishment of a robust reporting infrastructure enables proactive resolution of operational challenges and continuous improvement, ensuring exceptional experiences for both customers and employees.


A plan is in place to introduce a form visible only during store operations. Employees will be prompted to input details such as the user's email address and a brief description of the issue (optional). In the background, the system will retrieve a FullStory link and store this information in the backend system. Upon successful storage, an email notification will be sent to the relevant domain team.

Furthermore, a dashboard will be developed to display all information. This dashboard will provide the option to reassign issues to other domain teams if necessary.


https://user-images.githubusercontent.com/65896570/177631973-58a529eb-5017-415e-802b-89ae4cfef5f9.mp4

import { useState, useEffect } from 'react';

const getViewportWidth = () => {
  if (typeof window !== 'undefined') {
    return window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth;
  }
  return null;
};

export const useWindowDimension = () => {
  const [screenWidth, setScreenWidth] = useState(getViewportWidth());

  useEffect(() => {
    const handleResize = () => setScreenWidth(getViewportWidth());

    window.addEventListener('resize', handleResize);
    return () => window.removeEventListener('resize', handleResize);
  }, []);

  return screenWidth;
};

