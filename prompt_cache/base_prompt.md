Please create a "table" layout using HTML, TailwindCSS, and vanilla JS. Please opt for using TailwindCSS classes over JS whenever possible (such as for animations). Please create a full implementation of the specs below. I do not want any TODOs or feature/function placeholders.

This component has/is:


- Any references to right-clicking should have a touch-equivalent of a long-press. The provided JavaScript snippet for detecting long presses is a functional guideline. Feel free to adapt or generalize it logically across multiple elements or events as needed for clarity and maintainability:
    ```
        let timer;
        const LONG_PRESS_DURATION = 600; // milliseconds

        element.addEventListener('touchstart', (e) => {
        timer = setTimeout(() => {
            // Trigger the context menu or right-click equivalent action here
        }, LONG_PRESS_DURATION);
        });

        element.addEventListener('touchend', (e) => {
        clearTimeout(timer);
        });

        element.addEventListener('touchmove', (e) => {
        clearTimeout(timer); // Cancel if finger moves away
        });
    ```
- The text layout should be LTR by default, but still look great as RTL. I am not using any plugins for this, please use your existing talents to deal with this challenge
- The layout should detect RTL via the page’s dir attribute by default. However, allow manual override through a UI toggle, with the user's choice saved to local IndexedDB for future visits
- To better ensure RTL compatibility, avoid `pl-`, `pr-`, `ml-`, and `mr-` padding and margins and instead use `px-` and `mx-`, or if there's a more elegant solution, do that. 
- Icons should be as placeholder, use SVGs of squares, circles, triangles, stars, and hexagons
- If JavaScript is changing styles, it should be add/removing TailwindCSS classes, NOT adding/changing inline styles unless absolutely necessary (such as lack of TailwindCSS support)
- This component could get modified later so ensure there are guards to prevent errors in case certain elements are missing
- If there is any text that seems ambiguous, use placeholder text or guesses based on context in their place.
- All color choices should have a darkmode alternate using the `dark:` prefixed class
- Any animations should be smooth and punchy. This component should have depth to contrast it from its background.
- Anything you do should always have accessibility in mind, such as ARIA labels, keyboard navigation support, or high-contrast mode compatibility beyond standard Tailwind dark mode

If anything is ambiguous, please ask clarifying questions.