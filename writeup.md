# Write up

## Chatbot Functionality

The chatbot will be able to help seniors seeking career advice by asking them a series of questions about their interests to find a good potential career path. Firstly, the chatbot will greet the user explaining its purposes before beginning to evaluate the user. The chatbot will be able to suggest one of the following 5 career paths to the user based on their responses to questions relating to how much they are interested in code, design, and business. Firstly, the bot will ask the user which of the 3 interests areas intrigue the user the most. Afterwards, the chatbot will ask if they would like to focus primarily on that interest area if they would like their role to be more diverse. Based on that response, the chatbot will suggest one of the 5 career paths that best match the user's interests. Finally, the chatbot will thank the user for using the service and repeat the cycle if the user would like to try again.

## Computing Job Types

The chatbot is designed in a ay to suggest one of the following 5 computing job types to the user:

- UI/UX Designer
- Frontend Developer
- Project Manager
- Backend Developer
- System Architect

These career paths were choses because it gives the user a wide range of options depending on whether they would prefer to focus on design, business, or coding. The chatbot will suggest one of these 5 career paths to the user based on their responses to the chatbot's questions.

## Chatbot Code

udc.aiml

```
<?xml version="1.0" encoding="UTF-8"?>
<aiml>
    <category>
        <pattern>*</pattern>
        <template>Hello! Welcome! Congrats on all the hard work you have put in so
        far as you are nearing you degree completion!
        I can help you figure out a great career path post graduation.
        May I <set name="topic">help</set> you?
        </template>
    </category>

<topic name =""></topic>
<topic name="help">
  <category>
      <pattern>^ YES ^</pattern>
      <that></that>
      <template>Great! I can help you find a great <set name="topic">career</set>!
      Do you like coding, design, or business the most?
      </template>
  </category>

  <category>
      <pattern>^ NO ^</pattern>
      <template>No Problem! It sounds like you have it all figured <set name="topic">out</set>!</template>
  </category>
</topic>

<topic name="career">
    <category>
        <pattern>^ DESIGN ^</pattern>
        <template>Great. Yes or no. Do you want your career to purely focus on the design side?
        <learn>
            <category>
                <pattern>^ YES ^</pattern>
                <template>Great!You should check<set name="topic">out</set> a career as a: UX/UI Designer!
                </template>
            </category>
            <category>
                <pattern>^ NO ^</pattern>
                <template>No Problem! You should check<set name="topic">out</set> a career as a: Frontend Developer!</template>
            </category>
        </learn>
        </template>
    </category>
    <category>
        <pattern>^ BUSINESS ^</pattern>
        <template>Great. Yes or no. Do you want your career to purely focus on the business side?
        <learn>
            <category>
                <pattern>^ YES ^</pattern>
                <template>Great!You should check<set name="topic">out</set> a career as a: Project Manager!
                </template>
            </category>
            <category>
                <pattern>^ NO ^</pattern>
                <template>No Problem! You should check<set name="topic">out</set> a career as a: Systems Architect!</template>
            </category>
        </learn>
    </template>
    </category>
    <category>
        <pattern>^ CODING ^</pattern>
        <template>Great. Yes or no. Do you want your career to purely focus on the coding side?
        <learn>
            <category>
                <pattern>^ YES ^</pattern>
                <template>Great!You should check<set name="topic">out</set> a career as a: Backend Developer!
                </template>
            </category>
            <category>
                <pattern>^ NO ^</pattern>
                <template>No Problem! You should check<set name="topic">out</set> a career as a: Systems Architect!</template>
            </category>
        </learn>
    </template>
    </category>
</topic>



<topic name="out">
    <category>
        <pattern>*</pattern>
        <template>Thank you for using our service!<set name="topic"></set>
        </template>
    </category>
</topic>


</aiml>

```

interests.set

```
[["Coding"], ["Design"], ["Business"]]
```

careers.set

```
[["UI\/UX Designer"], ["Project Manager"], ["Frontend Developer"], ["Fullstack Developer"], ["Backend Developer"]]
```

## Training Cases and AIML Enhancements

Training cases were chosen to cover the following scenarios:

- A student in need of help who is passionate in coding and would like to focus on coding
- A student in need of help who is passionate in coding but doesn't want to purely focus on coding
- A student in need of help who is passionate in design and would like to focus on design
- A student in need of help who is passionate in design but doesn't want to purely focus on design
- A student in need of help who is passionate in business and would like to focus on business
- A student in need of help who is passionate in business but doesn't want to purely focus on business

These training cases were chosen because they covered the 3 main interest areas and the 2 possible responses for each interest area. The training cases were also chosen to cover the 5 possible career paths that the chatbot can suggest to the user.
The chatbot utilizes AIML to enhance the user experience by learning about the user's main area of interest and then by learning about whether the user would like to focus on that area of interest or not. The chatbot then uses this information to suggest one of the 5 career paths to the user.

In our first test case, the chatbot would first ask "Hello! Welcome! Congrats on all the hard work you have put in so far as you are nearing you degree completion! I can help you figure out a great career path post graduation. May I help you?" If the user responds with "YES", the chatbot would then ask "Great! I can help you find a great career! Do you like coding, design, or business the most?". If the user responds with "CODING", the chatbot would then ask "Great. Yes or no. Do you want your career to purely focus on the coding side?". If the user responds with "YES", the chatbot would then suggest "Great!You should check out a career as a: Backend Developer!". At this point, the chatbot would thank the user for using the service and repeat the cycle if the user would like to try again.

The rest of the training cases would go through a similar question and answer process with the chatbot. The following are the results of all the training cases:

- A student in need of help who is passionate in coding and would like to focus on coding
  - Input: "YES" "CODING" "YES"
  - Output: "Great!You should check out a career as a: Backend Developer!"
- A student in need of help who is passionate in coding but doesn't want to purely focus on coding
  - Input: "YES" "CODING" "NO"
  - Output: "No Problem! You should check out a career as a: Systems Architect!"
- A student in need of help who is passionate in design and would like to focus on design
  - Input: "YES" "DESIGN" "YES"
  - Output: "Great!You should check out a career as a: UX/UI Designer!"
- A student in need of help who is passionate in design but doesn't want to purely focus on design
  - Input: "YES" "DESIGN" "NO"
  - Output: "No Problem! You should check out a career as a: Frontend Developer!"
- A student in need of help who is passionate in business and would like to focus on business
  - Input: "YES" "BUSINESS" "YES"
  - Output: "Great!You should check out a career as a: Project Manager!"
- A student in need of help who is passionate in business but doesn't want to purely focus on business
  - Input: "YES" "BUSINESS" "NO"
  - Output: "No Problem! You should check out a career as a: Systems Architect!"

## Installation Manual

Steps to access the Chatbot:

1. Visit https://pandorabots.com/
2. Create an account or login to an existing account.
3. Visit https://home.pandorabots.com/dash/bot-directory# .
4. Search for "C951- Xavier Loera Flores" in the search bar.
5. Select the chatbot titled "C951- Xavier Loera Flores" with a description of "Career Assistance Chatbot created by Xavier Loera Flores".
6. A chat window will appear on the right side of the screen.
7. Type a message to begin the chatbot experience.

## Pandorabot Platform Strengths and Weaknesses

### Strengths

- The platform provides a web interface for creating and editing AIML files.
- The platform simulates the chatbot within a chat environment for testing inputs and responses.
- There exists GitHub integration for version control allowing users to use Git to backup their work.

For the most part, the platform strengths allow developers to work entirely within the Pandorabot platform so long as they are comfortable with the code editor. The platform also provides a chat environment for testing the chatbot which is useful for testing the chatbot's responses. The GitHub integration is also useful for version control and backup purposes.

### Weaknesses

- The integration with GitHub isn't perfect since pushing to a git repository will automatically delete any files not included within the Pandorabot workspace such as markdown files and images.
- The code editor is very basic and doesn't provide any robust error messages or auto-completion.
- The platform doesn't support uploading or viewing files types such as .md .pdf and .txt.

While a developer could potentially work entirely from within the Pandorabot editor, it is not ideal. There are several key developer experience features that come with developing natively on device that allow developers to have more control over their projects. Features such as choosing which files to commit to a git repository, having a more robust code editor, supporting more file types are important for developer experience.

## Chatbot Monitoring and Maintenance

The Chatbot can be monitored to by seeing how many students complete the chatbot experience and how many students are satisfied with the result given by the chatbot. Using this information, developers can introduce new questions and even career paths to cover more areas of interest and provide more accurate results for students.
