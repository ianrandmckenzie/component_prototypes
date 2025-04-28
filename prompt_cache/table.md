Please create a "table" layout using HTML, TailwindCSS, and vanilla JS. Please opt for using TailwindCSS classes over JS whenever possible (such as for animations). Please create a full implementation of the specs below. I do not want any TODOs or feature/function placeholders.

This component has/is:
- The standard usage of table elements like <table>, <th>, <tr>, <td>, etc.
- The table should be able to handle a variety of data types while still being responsive. Overflow-x should be scrollable, but only when necessary, and side scrolling button navigation should appear for those who do not have side scrolling (clicking scrolls over by 3 columns, or less if there are no additional columns to be seen) capability on their mouse or trackpad or device:
    HTML Tag | Data Type
    <td>, <th> | string, integer, float, boolean, percentage, datetime, date
    <img>, <video>, <audio> | string (image URL/path)
    <input> | string, integer, float, date
    <a> | string (URLs, email, phone)
    <time> | datetime, date, string
    <span>, <p> | string
- Cells have a default height of `h-16`
- The table should have "input mode" where all tables can be edited. When input mode is activated, the table is saved to local IndexedDB as a JSON unless "api mode" is activated in which the JSON is sent as a POST to a placeholder URL — there is obviously a GET endpoint as well if "api mode" is active which pulls data from there instead
- If the API endpoint returns an error or is unreachable, gracefully revert to using local IndexedDB or placeholder data, whichever is available.
- When in input mode, there is a sidebar that provides row/column/cell editing options. Please logically infer these options and implement them in all the ways you understand how spreadsheet editors work.
- When clicking on a cell/column heading/row heading in input mode, it highlights the cell/column/row with a border color and when the sidebar editor options are used, it applies to the selected cell/column/row
- Please ensure we are only editing the row from clicking the row "handlebar" on the far left (far right on RTL)
- Please ensure we are only editing the column from clicking the column "handlebar" on the at the top
- Please create 3 different datasets for yourself to work with. Anything requiring URLs will be adjusted by me so please use "#" as the href or src for those.
- When in "Input mode" data types for cells are inferred by the data existing within them
- When cells are edited, they continue to be inferential and change as needed as they are edited
- When right-clicking (or long-pressing) a cell to change its data type, present a small dialog with options logically determined by you (e.g., select input type from a dropdown, enter URL, upload file placeholder, etc.). This must include media type options like image, video, and audio.
    * This must also include a currency option where the currency option, on hover, presents a popout menu for their desired currency character, such as $, £, ¢, ¥, etc.
    * For media options in "input mode" the input is split 50/50. The left side is "Put a URL to your media here" and the right side is an upload button which adds the blob as the URL. When not in input mode, the media is shown within its standard tag based on the media type (image, audio, or video)
- When editing a cell in input mode, ensure the input is the same background color as the cell
- "Input mode" is toggled by a checkbox at the top right of the page
- The JSON structure can be logically determined by you
- When the JSON structure is saved to local IndexedDB, the table uses local IndexedDB instead of the placeholder data
- The table should have tabs to navigate to other tables. When "input mode" is enabled, there is a "+" tab that allows the user to create a new table. These tabs can have their names edited if the tab is double-clicked/tapped instead of single click/tap which opens the tab within the table view. When a new tab is created, there are 3 empty rows and 4 empty columns as placeholder. When adding a new table, the user is prompted to give the table a name
- When editing the table name from a double-click, the input is inline and pressing the enter/return key or clicking away saves that table name
- Whenever a handlebar or cell is clicked away from, the editor sidebar context should be cleared to prevent user confusion
- "Input mode" gives the ability to create new tabs and rows with a "+" for column on the far right of the columns and "+" for row at the bottom of the rows. Right-clicking on the border between a column or row presents a dialog which lets them click "Add new column" on vertical borders, "Add new row" on horizontal borders, or both options when clicking a cross-section of border
- Ensure when in "Input mode" the table column headings are editable. When the the is right-clicked, the data type dialog is also opened, and when chosen, the rows below are attempted to be cast into that data type. If there is an error, it fallsback to whatever data was there previously. For example, if the column is cast into integer, but the cell has "abcxyz" it will simply leave that cell as a string with "abcxyz"
- Column and rows should have their width and height editable by left-click and dragging from the border. When using touch/mobile, this behavior will instead fallback to the long-press behavior and instend has the additional dialog to "Resize column" or "Resize row" — when selected the border highlights into "resize mode" and they can then drag to resize. When released, the "resize mode" ends
- Table cells should have a min-width of `w-16` when resized by the user. User sized cells/rows should always supercede automatic resizing when new tables/rows are created
- When editing a cell, the tab keys changes the focused input to the next column (unless there are no more columns in that row, at which point it focuses the first column of the next row)
- Column row widths should remain the same width as their existing width when an input is selected
- Table cells should should retain their height/width when new columns/rows are added
- Newly created columns should have the `w-48` class until they are optionally resized by the user
- Newly created columns/rows can default to blank cells, and their types will be inferred as soon as data is entered. When clicking a cross-section, present clearly distinct options for adding either or both rows and columns
- Implement clear keyboard navigation (arrow/tab keys between cells, Enter/Esc to edit or close dialogs, context menu key to open cell dialogs). If additional shortcuts improve usability, feel free to logically include them


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
