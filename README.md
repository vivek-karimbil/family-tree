# Family Tree Editor

A single page application for creating and editing a family tree. This uses [OrgChart.js](https://github.com/dabeng/OrgChart) for tree visualization and editing. Work in progress i saved in bowser storage, while the charts can be exported and imported from local JSON files.

## Features

- ✅ **Add/Edit/Delete Family Members** - Simple form-based interface
- ✅ **Organize by Parent-Child Relationships** - Build hierarchical structures
- ✅ **Mark Outsiders** - Flag people who married into the family
- ✅ **Export/Import JSON** - Download and upload family tree data
- ✅ **Live Preview** - View your family tree with OrgChart.js
- ✅ **Local Storage** - Auto-save your work in the browser
- ✅ **JSON Viewer** - Inspect the raw data in real-time

## Getting Started

### Open the Editor

Simply open `FamilyTreeEditor.html` in your web browser:
```
Double-click editor.html
```

Or:
```
Right-click FamilyTreeEditor.html → Open with → Your favorite browser
```

## How to Use

### 1. Adding Family Members

1. Fill in the form fields:
   - **Name**: The person's full name
   - **Relationship**: Their relationship/role (e.g., "Father", "Daughter", "Son-in-Law")

2. Click **"Add Member"** button
3. The member appears in the "Family Members" list

### 2. Editing Existing Members

1. Click on a member in the "Family Members" list to select them
2. Their details appear in the form
3. Make changes to any field
4. Click **"Update Member"** button

### 3. Setting Parent-Child Relationships

To link a child to a parent:
1. Know the parent's ID (e.g., "1")
2. When adding/editing a child, enter the parent ID in the "Parent ID" field
3. Save the member

### 4. Exporting Data

1. Click **"📥 Export JSON"** button
2. A `family-tree.json` file downloads to your computer
3. This file can be used in other applications or shared

### 5. Importing Data

1. Click **"📤 Import JSON"** button
2. Select a previously saved or created `family-tree.json` file
3. The family tree loads into the editor

### 6. Previewing the Family Tree

1. Click **"View as Family Tree"** button
2. A new window opens showing an interactive OrgChart visualization
3. You can pan (drag), zoom, and explore the tree
4. Click "← Back to Editor" to return to editing

### 7. Viewing Raw JSON

1. Click **"View JSON"** button
2. A new window opens showing the complete JSON data structure
3. This is useful for understanding the data format or copying it elsewhere

## Data Format

The family tree data is stored as a JSON array of member objects:

```json
[
  [
    {
      "id": "1",
      "name": "Father Doe",
      "relationship": "Father"
      children: [
          [
            {
              "id": "3",
              "name": "Tom Doe",
              "relationship": "Son"
            }
          ]
        ]
    },
    {
      "id": "2",
      "name": "Mother Doe",
      "relationship": "Mother"
      "outsider": true
    }

]
```

## Auto-Save Feature

Your work is automatically saved to the browser's **Local Storage**. When you close and reopen, your data will still be there! This is to safeguard your edits, bod export your tree periodically to have a backup of your work.

> **Note**: Local Storage is specific to each browser and computer. To backup your data, regularly use the **Export JSON** feature.

## Exporting for Use

If you want to use your created family tree with the existing HTML visualization:

1. Edit your family tree in `editor.html`
2. Click **"📥 Export JSON"** to download your `family-tree.json`
3. Copy the JSON data from the JSON viewer
4. Open the saved JSON file in a text editor

## Tips & Tricks

- **IDs are Important**: Use simple numeric IDs (1, 2, 3...) for easier management
- **Parent-Child Links**: Always make sure child's parent ID exists
- **Outsiders**: Mark anyone who married into the family as an "outsider" (affects coloring in preview)
- **Backup**: Regularly export your JSON to secure backups
- **Reorganize**: You can always change parent IDs to reorganize the tree structure

## Browser Compatibility

Works in all modern browsers:
- Chrome/Edge (recommended)
- Firefox
- Safari
- Opera

## Technical Details

The editor uses:
- Vanilla JavaScript (no dependencies required)
- HTML5 Local Storage for persistence
- OrgChart.js library for visualization (downloaded from CDN)
- jQuery (loaded from CDN for OrgChart compatibility)

## Troubleshooting

**My data disappeared after closing the browser**
- Local Storage was cleared or disabled. Use "Export JSON" regularly to backup.

**The "View as Family Tree" button doesn't work**
- Make sure you have at least one member added and an internet connection (for loading OrgChart.js)

**IDs are showing as duplicates**
- Check the JSON view and ensure each member has a unique ID

**Parent-child relationships not showing**
- Verify the child's "parentId" matches the parent's "id" exactly

## File Listing

```
FamilyTree/
├── README.md                   (This file)
├── FamilyTreeEditor.html       (Helper functions)
├── data/                       (Data folder for storage)
```

---

**Created for organizing and visualizing family relationships in an easy, web-based format!**
