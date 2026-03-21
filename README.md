# Family Tree Editor

A web-based application for creating and editing JSON family tree data that can be used with OrgChart.js visualization.

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

### Field Descriptions

- **id**: Unique identifier (auto-generated, but you can set custom ones)
- **name**: Person's full name
- **relationship**: Their relation/role in the family tree
- **gender**: "male", "female", or "other"
- **parentId** (optional): The ID of their parent
- **outsider** (optional): Set to `true` if they married into the family

## Using TreeWeb.js

The `TreeWeb.js` file contains a `FamilyTreeManager` class for programmatically managing family tree data.

### Example Usage

```javascript
// Create a manager
const tree = new FamilyTreeManager();

// Add members
const grandpa = tree.addMember('George', 'Grandfather', 'male');
const grandma = tree.addMember('Mary', 'Grandmother', 'female', null, false);
const dad = tree.addMember('David', 'Father', 'male', '1');

// Update a member
tree.updateMember('1', { title: 'Great Grandfather' });

// Get all members
console.log(tree.getAll());

// Export as JSON
console.log(tree.toJSON());

// Build OrgChart data
const chartData = tree.buildOrgChartData();
```

### Available Methods

- `addMember(name, title, gender, parentId, outsider)` - Add a member
- `updateMember(id, updates)` - Update a member
- `deleteMember(id)` - Delete a member
- `getMember(id)` - Get member by ID
- `getChildren(parentId)` - Get all children of a member
- `getParent(memberId)` - Get parent of a member
- `getAll()` - Get all members
- `toJSON()` - Export as JSON string
- `loadFromJSON(data)` - Load from JSON array
- `buildOrgChartData()` - Build OrgChart compatible structure
- `getStats()` - Get tree statistics
- `clear()` - Clear all members

## Auto-Save Feature

Your work is automatically saved to the browser's **Local Storage**. When you close and reopen `editor.html`, your data will still be there!

> **Note**: Local Storage is specific to each browser and computer. To backup your data, regularly use the **Export JSON** feature.

## Exporting for Use with Gollamudi Family.html

If you want to use your created family tree with the existing HTML visualization:

1. Edit your family tree in `editor.html`
2. Click **"📥 Export JSON"** to download your `family-tree.json`
3. Copy the JSON data from the JSON viewer
4. Open `Gollamudi Family.html` in a text editor
5. Find the `var datascource = [` line
6. Replace the entire `datasource` array with your exported data
7. Save and open the HTML file in a browser to see your family tree

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
├── editor.html                 (Main editor app - Open this!)
├── TreeWeb.js                  (Helper functions)
├── Gollamudi Family.html       (Example visualization)
├── data/                       (Data folder for storage)
└── README.md                   (This file)
```

---

**Created for organizing and visualizing family relationships in an easy, web-based format!**
