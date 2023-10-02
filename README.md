# Game of Thrones Characters Showcase with Favorite Selection Feature

## Introduction
The goal of this task is to display Game of Thrones Characters and allow user to choose their favorites.

### Used Technologies
- TypeScript
- Vue 3 (Composition API)
- CSS

## Tasks
1. Fetch characters from: [https://thronesapi.com/api/v2/Characters](https://thronesapi.com/api/v2/Characters).
2. On the list, display all the characters **NOT** from *House Lannister*.
3. Each list item should contain: Character name, photo and a star icon.
4. If the character is a *Lady* or a *Lord*, place crown icon next to the character’s name.
5. Hovering over the crown icon shall display a tooltip with the character’s full title.
6. Implement favorite character functionality:
   - Add a clickable star icon for each character in the Game of Thrones Characters list.
   - When the user clicks on the star icon, the character becomes a *favorite* and appears in *My Favorites* list. Clicking on the star icon (filled) will remove the character from the *My Favorites* list.
   - Each row in *My Favorite* list should look like the rows in Game of Thrones Characters, including the star icon and its behavior.
7. At the top of the page, display one King and one Queen.
8. Add input to filter My Favorite list.

## Bibliography
- [Game of Thrones API Documentation](https://thronesapi.com/swagger/index.html?urls.primaryName=Game%20of%20Thrones%20API%20v2)
- [Vue Documentation](https://vuejs.org/guide/introduction.html)
