# Website for working with resumes

This site was written for PROD olympiad. The task was to create 3 pages:
1) Resume input page. 
2) Resume showing page.
3) Resume list page.

Code pages: [First](https://github.com/pluffohman/ResumeFrontend/blob/master/index.html), 
[Second](https://github.com/pluffohman/ResumeFrontend/blob/master/resume_output.html), 
[Third](https://github.com/pluffohman/ResumeFrontend/blob/master/resume_list.html)

## Mechanics
The webpages were wtitten on clear HTML, CSS and JavaScript. No third party libraries were used.
On the first page we can't create resume if block $Name$ is clear. When we click the button $Create resume$, our data is being transferred to the second page in the __URL__.
I used this method only with second page. From the second to the third and from the third to the first data is being saved in the __local JS storage__.

## Third page...

Here, on the third page we can make these manipulations with our resumes:
 - Copy them. After clicking $Copy$ button the checkbox window is showed, and we should choose boxes which we want to copy.
After choosing and clicking $OK$ button we would be redirected on the first page, and blocks will be field with the copied information.
- Deleting them. We also have checkboxes next to resume titles, we can click on them, and after clicking $Delete$ $chosen$ button, chosen resumes will be deleted from the local storage.
- View them. After clicking $View$ button, we would be redirected to the second page and resume would be shown. 
Here I would like to remind you that data is transferred to the second page using $url$ method.

## Examples of redirecting and transferring data

```javascript
    const queryString = new URLSearchParams(resume).toString();
    window.location.href = `resume_output.html?${queryString}`;
```

```javascript
    function saveResume() {
    const resumeData = {
        fullName: document.getElementById('fullName').innerText,
        birthdate: document.getElementById('birthdate').innerText,
        city: document.getElementById('city').innerText,
        phoneNumber: document.getElementById('phoneNumber').innerText,
        email: document.getElementById('email').innerText,
        interests: document.getElementById('interest1').innerText,
        languages: document.getElementById('language1').innerText,
        workExperience: document.getElementById('workPlace1').innerText,
        workStartDate: document.getElementById('workStartDate1').innerText,
        workEndDate: document.getElementById('workEndDate1').innerText,
        education: document.getElementById('educationPlace1').innerText,
        educationStartDate: document.getElementById('educationStartDate1').innerText,
        educationEndDate: document.getElementById('educationEndDate1').innerText,
        course: document.getElementById('course1').innerText,
        courseStartDate: document.getElementById('courseStartDate1').innerText,
        courseEndDate: document.getElementById('courseEndDate1').innerText,
        description: document.getElementById('resumeDescription').innerText
    };

    let savedResumes = JSON.parse(localStorage.getItem('savedResumes')) || [];
    savedResumes.push(resumeData);
    localStorage.setItem('savedResumes', JSON.stringify(savedResumes));
    window.location.href = "resume_list.html";
}
```
