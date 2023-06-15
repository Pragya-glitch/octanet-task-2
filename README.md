# octanet-task-2
&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;meta http-equiv=&quot;X-UA-Compatible&quot; content=&quot;IE=edge&quot;&gt;
    &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;&gt;
    &lt;title&gt;Task List 2021&lt;/title&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;main.css&quot; /&gt;
&lt;/head&gt;
&lt;body&gt;
   
    &lt;header&gt;
        &lt;h1&gt;To-do-List 2023&lt;/h1&gt;
        &lt;form id=&quot;new-task-form&quot;&gt;
            &lt;input
                type=&quot;text&quot;
                name=&quot;new-task-input&quot;
                id=&quot;new-task-input&quot;
                placeholder=&quot;What do you want to have ?&quot; /&gt;
            &lt;input
                type=&quot;submit&quot;
                id=&quot;new-task-submit&quot;
                value=&quot;Add task&quot; /&gt;
        &lt;/form&gt;
    &lt;/header&gt;
    &lt;main&gt;
        &lt;section class=&quot;task-list&quot;&gt;
            &lt;h2&gt;Tasks&lt;/h2&gt;
            &lt;div id=&quot;tasks&quot;&gt;
                &lt;!-- &lt;div class=&quot;task&quot;&gt;
                    &lt;div class=&quot;content&quot;&gt;
                        &lt;input
                            type=&quot;text&quot;
                            class=&quot;text&quot;
                            value=&quot;A new task&quot;
                            readonly&gt;
                    &lt;/div&gt;
                    &lt;div class=&quot;actions&quot;&gt;
                        &lt;button class=&quot;edit&quot;&gt;Edit&lt;/button&gt;
                        &lt;button class=&quot;delete&quot;&gt;Delete&lt;/button&gt;
                    &lt;/div&gt;
                &lt;/div&gt; --&gt;
            &lt;/div&gt;
        &lt;/section&gt;
        &lt;/main&gt;
    &lt;script src=&quot;main.js&quot;&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;

 main.css
:root {
    --dark: #374151;
    --darker: #1F2937;
    --darkest: #111827;
    --grey: #6B7280;
    --pink: #EC4899;
    --purple: #8B5CF6;
    --light: #EEE;
}
* {
    margin: 0;
    box-sizing: border-box;
    font-family: &quot;Fira sans&quot;, sans-serif;
}
body {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    color: #FFF;
    background-color: var(--dark);
}
header {
    padding: 2rem 1rem;
    max-width: 800px;
    width: 100%;
    margin: 0 auto;
}
header h1{
    font-size: 2.5rem;
    font-weight: 300;
    color: var(--grey);
    margin-bottom: 1rem;
}
#new-task-form {
    display: flex;;
}
input, button {
    appearance: none;
    border: none;
    outline: none;
    background: none;
}

#new-task-input {
    flex: 1 1 0%;
    background-color: var(--darker);
    padding: 1rem;
    border-radius: 1rem;
    margin-right: 1rem;
    color: var(--light);
    font-size: 1.25rem;
}
#new-task-input::placeholder {
    color: var(--grey);
}
#new-task-submit {
    color: var(--pink);
    font-size: 1.25rem;
    font-weight: 700;
    background-image: linear-gradient(to right, var(--pink), var(--purple));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    cursor: pointer;
    transition: 0.4s;
}
#new-task-submit:hover {
    opacity: 0.8;
}
#new-task-submit:active {
    opacity: 0.6;
}
main {
    flex: 1 1 0%;
    max-width: 800px;
    width: 100%;
    margin: 0 auto;
}
.task-list {
    padding: 1rem;
}
.task-list h2 {
    font-size: 1.5rem;
    font-weight: 300;

    color: var(--grey);
    margin-bottom: 1rem;
}
#tasks .task {
    display: flex;
    justify-content: space-between;
    background-color: var(--darkest);
    padding: 1rem;
    border-radius: 1rem;
    margin-bottom: 1rem;
}
.task .content {
    flex: 1 1 0%;
}
.task .content .text {
    color: var(--light);
    font-size: 1.125rem;
    width: 100%;
    display: block;
    transition: 0.4s;
}
.task .content .text:not(:read-only) {
    color: var(--pink);
}
.task .actions {
    display: flex;
    margin: 0 -0.5rem;
}
.task .actions button {
    cursor: pointer;
    margin: 0 0.5rem;
    font-size: 1.125rem;
    font-weight: 700;
    text-transform: uppercase;
    transition: 0.4s;
}
.task .actions button:hover {
    opacity: 0.8;
}
.task .actions button:active {

    opacity: 0.6;
}
.task .actions .edit {
    background-image: linear-gradient(to right, var(--pink), var(--purple));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}
.task .actions .delete {
    color: crimson;
    main.js
    window.addEventListener(&#39;load&#39;, () =&gt; {
const form = document.querySelector(&quot;#new-task-form&quot;);
const input = document.querySelector(&quot;#new-task-input&quot;);
const list_el = document.querySelector(&quot;#tasks&quot;);
form.addEventListener(&#39;submit&#39;, (e) =&gt; {
e.preventDefault();
const task = input.value;
const task_el = document.createElement(&#39;div&#39;);
task_el.classList.add(&#39;task&#39;);
const task_content_el = document.createElement(&#39;div&#39;);
task_content_el.classList.add(&#39;content&#39;);
task_el.appendChild(task_content_el);
const task_input_el = document.createElement(&#39;input&#39;);
task_input_el.classList.add(&#39;text&#39;);
task_input_el.type = &#39;text&#39;;
task_input_el.value = task;
task_input_el.setAttribute(&#39;readonly&#39;, &#39;readonly&#39;);
task_content_el.appendChild(task_input_el);
const task_actions_el = document.createElement(&#39;div&#39;);
task_actions_el.classList.add(&#39;actions&#39;);
const task_edit_el = document.createElement(&#39;button&#39;);
task_edit_el.classList.add(&#39;edit&#39;);
task_edit_el.innerText = &#39;Edit&#39;;
const task_delete_el = document.createElement(&#39;button&#39;);
task_delete_el.classList.add(&#39;delete&#39;);
task_delete_el.innerText = &#39;Delete&#39;;
task_actions_el.appendChild(task_edit_el);
task_actions_el.appendChild(task_delete_el);
task_el.appendChild(task_actions_el);
list_el.appendChild(task_el);
input.value = &#39;&#39;;
task_edit_el.addEventListener(&#39;click&#39;, (e) =&gt; {
if (task_edit_el.innerText.toLowerCase() == &quot;edit&quot;) {
task_edit_el.innerText = &quot;Save&quot;;
task_input_el.removeAttribute(&quot;readonly&quot;);
task_input_el.focus();
} else {
task_edit_el.innerText = &quot;Edit&quot;;
task_input_el.setAttribute(&quot;readonly&quot;,

&quot;readonly&quot;);
}
});

task_delete_el.addEventListener(&#39;click&#39;, (e) =&gt; {
list_el.removeChild(task_el);
});
});
});
