# Web accessibility notes

Web accessibility (often reffered as A11y) is a way to design apps so that users with certain dissabilities can understand and use them. 
The W3C Web Accessibility Initiative (WAI) develops accessibility standards. The Web Content Accessibility Guidelines (WCAG) is one of those guidelines. Their goal is to provide a single standard for web content accessibility which will meet the needs of individuals, organizations, and governments internationally.

Anyone who wants to use the Web must have content that is:

* perceivable - Information and user interface components must be presentable to users in ways they can perceive. This means that users must be able to perceive the information being presented (it can't be invisible to all of their senses)
* operable - User interface components and navigation must be operable. This means that users must be able to operate the interface (the interface cannot require interaction that a user cannot perform)
* understandable - Information and the operation of user interface must be understandable. This means that users must be able to understand the information as well as the operation of the user interface (the content or operation cannot be beyond their understanding)
* robust - Content must be robust enough that it can be interpreted reliably by a wide variety of user agents, including assistive technologies. This means that users must be able to access the content as technologies advance (as technologies and user agents evolve, the content should remain accessible)

If any of these are not true, users with disabilities will not be able to use the Web.

There are four types of disabilites:
* motor
* cognitive
* auditory
* visual


## Useful links
* Quick reference to Web Content Accessibility Guidlines (WCAG) and Levels: requirements and techniques -  https://www.w3.org/WAI/WCAG21/quickref/
* Vue a11y - https://github.com/vue-a11y
* Accessibility checklist - https://github.com/springernature/frontend-playbook/blob/master/accessibility/accessibility-checklist.md
* Frontend checklist - https://frontendchecklist.io/
* A11y project checklist - https://a11yproject.com/checklist/
* Contrast ratio checker - https://webaim.org/resources/contrastchecker/
* ARIA attributes - https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA
* Accessibility Audit Rules - https://github.com/GoogleChrome/accessibility-developer-tools/wiki/Audit-Rules#-ax_text_02--images-should-have-an-alt-attribute-unless-they-have-an-aria-role-of-presentation

## Audit tools
* https://web.dev/measure/
* https://webaim.org/
* https://developers.google.com/web/tools/lighthouse
* https://chrome.google.com/webstore/detail/axe-web-accessibility-tes/lhdoppojpmngadmnindnejefpokejbdd


## Most common ARIA attributes
They are split in 3 categories: roles, properties and states.

* ```aria-label``` - svg inside anchor tag (facebook button) e.g. "Follow company on facebook"
* ```aria-labelledby``` - reference for caption
* ```aria-expanded``` - mostly for accordions and hamburgers
* ```aria-current``` - current page/link/step/date/location. Useful because screen readers detect them and it's better than toggling classes
* ```aria-hidden``` - telling screen readers what element to skip (not to announce it)
* ```aria-describedby``` - recieves a reference to a (mostly hidden) element and reads the content of it. Difference between this and ```aria-label``` is that screen reader will just read the ```aria-label``` word by word, and in case of ```aria-describedby``` it will read the native text of the element and then the referenced content.
* ```aria-invalid``` - will cause the screen reader to announce "invalid" when that control gets in focus
* ```aria-required``` - will cause the screen reader to announce "required" when that control gets in focus
* ```aria-described``` - recieves a reference to a (mostly hidden) element and reads the instructions provided in that element.  

## Arguments for implementing

* larger target audience 
* not just for disabled people, it's also for people who can't user the mouse, who can't see, who can't see colors etc.
* if your target audience is 20 year olds, there are also 20 year olds that cannot use sites that don't have accessibility implemented
* explain what that means for non tech savy clients
* don't treat accessibility as something extra for the project, so just add it in the "package"
* if it's done from the very beginning, it doesn't cost almost nothing more
* business advantages - drive innovation, enhance your brand, extend market reach (1.3 bilion people with disabilities), minimize legal risk (requirement for all government and EU websites)

## Accessible content

### Text transcripts
Text transcripts allow user s to access a textual representation for video and adutio-only content. It is useful for hearing, visual and cognitive disabilities.

### Audio descriptions

Audio descriptions provide an audio-based description of meningful visual elements in video content. It is tintended for users with visual impairments. They provide a description of meaningful info about actions, characters, scene changes or on-screen text. Example: explaination of a graph. Imagine a narator explaining a scene from a video or a movie.

### Captions

Captions provide a synchronous textual representation of spoken words in video content. Intended for users who cannot access the audio, but can still view the content. Often they include the speakers name in the square brackets, or the speakers tone like yelling or whispering. 

### The use of color

Color blindness manifests in many ways. Be careful when using colors.

* users should always be able to understand information if all of the colors were removed 
* graphs and charts can be problematic - we have to use patterns and styles
* maps can also be problematic - usually work on click when some high contrast color will appear on the map
* color contrast ratios are important - they ensure that the content is visible to users with low vision or color blindness (text under 18pts 4.5:1, text above 18pts 3:1) 

### Accessible Forms

* they don't benefit just the disabled users
* forms in general have to be simple and intuitive
* unaccessible forms can be difficult to complete, because users won't be able to understand them
* importance of the label tag - it is a text based description of a form element 
* importance of the for attribute - it sould match the ID of the form element
* fieldset element group related controls together and it allows non sighted users to understand group parameters 
* the legend element provides a title for the fieldset of one or multiple elements, e.g. "Credit card details". It should be the first element in the fieldset element

Be careful with errors in forms 
* they are found when certain fields are not completed or invalid 
* errors should inform the user about that 
* error recovery process should alert the user and enable easy access to fields and controls and enable the resubmission of the form
* errors often can be found on the top of the page because screen readers read from top to bottom 
* keyboard accessibility is important in forms, so that users can use tab, shift and enter keys

### Semantic HTML
It is important to use appropriate HTML elements and make the website semanticly correct. Using wrong elements for wrong things is bad for accessibility. Using elements in a wrong way can confuse the screen readers and people will have bad expirience. 

### Headings
Headings structure as a rule and they should be used as following:
* h1 - main page heading
* h2 - article heading
* h3 - section heading
* h4 - sub-section heading 1
* h5 - sub section heading 2
* h6 - sub section heading 3

### Colors and accessibility
Contrast is important for colorblind people because it allows them to read something on a particular background. It is importatn not to rely solely on color to transfer meaning (e.g. red for error, yellow for warning). We have to make it easier with other things like icons. Also, enlarging the text can give you better contrast - it's not just the colors!

### Accessible images
Background images are accessible OOTB; screen readers will just skip them and you can't give them an aria attribute.
If you have an image in a ```img``` tag, then you have to add the alt attribute (at least an empty one, so that screen readers don't read the ```src```). Always put the ```alt``` attribute to images (especially if the image is rerouting the user).

### Bypass Blocks (skiplinks)
Level A mechanism for bypassing blocks of content that are repeated on the web page. Mostly divs/links that are invisible by default, but by pressing tab they become visible and allows the user to skip to a particular part of the page (e.g. main content or contact form). This way user will have to use tab 2-3 times instead of 10.

### Hamburgers
Example 1: https://codepen.io/dekadentno/pen/qBOxXZM
Example 2: https://codepen.io/dekadentno/pen/XWmZaKV
We have to make sure they are semantic and big enough for human fingers to tap them. 

### Contact forms
Do not avoid using fieldsets and legents to group inputs and never use placeholders for labels! Try avoiding placeholders and be sure to properly mark required fields with ```aria-required``` (remember that JS validation is not possible if using ```required``` attribute in HTML. Try to use descriptive buttons ("Send message" instead of "Submit"). Also, you can use a star ```*``` for marking required fields, but make sure you use ```aria-hidden``` on it so that screen readers doesn't announce it. It is important to test the form with tab and make sure that by pressing tab the next input is focused, and not something else. Try avoiding CAPTCHAs because they are unaccessible for most users.

### Icons
All icons shuld have text next to them. Only in case of social media buttons, icons without text are acceptable. It is okay to hide icons (```aria-hidden```) for screen readers because they are not necessary to be read (because in most cases they are use to help transfer meaning), especially if that icon is an svg. But still, make sure that the icons are visible enough and that they have the right contrast.

### Links
Be careful when using ```target="_blank"``` on links, because it complicates accessibility. If you have to use it, the best way is to add an icon that will be used for links that will open a new tab, and make sure to add an ```aria-label``` (or ```aria-describedby```) on that icon so that screen reader announces it. Try not to leave underlined style on links, because that's the native behaviour of links and people are already used to it.
A bad example of links is an often used "click here" link. Make sure links are as descriptive as possible by rewriting your sentance.
