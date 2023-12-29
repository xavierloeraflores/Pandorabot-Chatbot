# Write up

## Chatbot Functionality

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
                <template>Great!You should check<set name="topic">out</set> a career as a: Backend Developmer!
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

## Installation Manual

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
