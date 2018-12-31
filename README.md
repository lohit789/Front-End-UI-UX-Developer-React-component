Step 1. Starting off with create-react-app

Let’s create a React app usingcreate-react-app CLIto create new React app.This CLI is actually built by Facebook for developers to create a well structured React application.

To install the create-react-app tool use the below command:
1 npm install -g create-react-app
Once you do so use below command to create a new application:
1 reate-react-app accordion

Now this command will create a new folder called accordion and download the all necessary dependencies. 
To run the application in development mode you should use
npm start and 
run the application in production mode you should use
npm run build.

Since we are creating a dynamic accordion, we will axios to fetch data from the mock API server, just to generate fake data. 
You can install axios using npm , Below is my package.json file:
package.json:
{
  "name": "accordion",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "axios": "^0.17.0",
    "react": "^16.0.0",
    "react-dom": "^16.0.0",
    "react-scripts": "1.0.17"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject"
  }
}
I normally prefer to create my all components in a separate folder.Here I have created a folder named as component and I will create my accordion component inside it. Below is our project’s folder structure.

Step 2. Creating a Dynamic accordion menu using ReactJs

Here we will create two files Accordion.js, Section.js and We will use App.js and index.css created by create-react-app CLI. Let’s start off by modifying App.js:
App.js:

/* 
* Dynamic accordion menu using ReactJs Tutorial
* @author Lohit Kumar 
*/
import React, { Component } from 'react';
import './App.css';
import Accordion from './components/Accordion';

class App extends Component {
  render() {
        return (
            <Accordion/>
        );
    }
}

export default App;
Explanation:

Nothing too fancy here, I have just imported Accordion component and that’s it.

Step 3. Generating a Fake data and calling Accordion

Let’s write something inside the Accordion.js, In this component, we will call another component named as Section. The Section component is part of Accordion component.
Explanation:

1.Imports:- We have three imports here first two are the node modules and the Third one is<Section>component.

2.constructor(props):-Inside the constructor method, there’s stats and props And If you work with React I assume you are familiar with it.

3.componentDidMount():- We will generate fake data from Mock REST API.

4.renderLoading():- This method will render the Loading Text till the previous method gets data from Mock API server.

5.renderError():- This method will render the error message on the Page.

6.renderPosts():- This method will call the<Section/>component and render the Accordion in a Loop.

Step 4: Displaying the Accordion
Now open the Section.js and write down the below code. In the<Section/>component, we will handle the hide and show part of Accordion. As I said earlier the<Section/>component will be called by Accordion component in a loop.

Section.js:
/* 
* Dynamic accordion menu using ReactJs Tutorial
* @author Lohit Kumar 
*/

import React from 'react';
class Section extends React.Component {

    constructor(props) {
        super(props);

        this.state = {
            open: false,
            className: 'accordion-content accordion-close',
            headingClassName: 'accordion-heading'
        };

        this.handleClick = this.handleClick.bind(this);
    }

	/*
	* Handling the click event
	*/
    handleClick() {
        const { open } = this.state;
        if (open) {
            this.setState({
                open: false,
                className: "accordion-content accordion-close",
                headingClassName: "accordion-heading"
            });
        } else {
            this.setState({
                open: true,
                className: "accordion-content accordion-open",
                headingClassName: "accordion-heading clicked"
            });
        }
    }

    /*
* Ceating the single accordion here.
*/
    render() {

		/*
		* Using destructuring to extract the 'error' from state.
		*/
        const post = this.props.post;
        const { className } = this.state;
        const { headingClassName } = this.state;
        console.log(headingClassName);
        return (
            <div className="parent-accordion">
                <div className={headingClassName} onClick={this.handleClick}>
                    {post.title}
                </div>
                <div className={className}>
                    {post.body}
                </div>
            </div>
        );
    }

}

export default Section;

Explanation:

ThehandleClick()method will add and remove the class name from the Elements. The render method() will return the single Accordion along with hiding and show functionality and So now we have successfully implemented Dynamic Accordion using ReactJs.

Steps For run the Application:

To Install all Node Modules to the folder we need 
npm install

To run the application in development mode you should use
npm start

To run the application in production mode you should use
npm run build

we will axiosto fetch data
You can install axios using npm


System Local URL:
http://localhost:3000 
