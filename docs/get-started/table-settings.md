#### Example Table Settings
If our table settings were:
```
const tableSettings = {
    tableID: 'DataTable',
    keyField: 'ref_id',
    tableColumns: [
        {
            title: 'Ref',
            key: 'ref_id',
            filter: 'NumberFilter',
            defaultValue: { comparator: '=' },
        },
        {
            title: 'First Name',
            key: 'first_name',
        },
        {
            title: 'Surname',
            key: 'surname',
        },
        {
            title: 'Type',
            key: 'type',
            filter: 'SelectFilter',
            filterOptions: {
                Add: 'Add',
                Amend: 'Amend',
                Remove: 'Remove',
            },
        },
    ],
};
```

Then the tableSettings post parameter would contain a corresponding json object:
```json
{
  "tableID":"DataTable",
  "keyField":"ref_id",
  "tableColumns":[
    {
      "title":"Ref",
      "key":"ref_id",
      "filter":"NumberFilter",
      "defaultValue":{"comparator":"="}
    },
    {
      "title":"First Name",
      "key":"first_name"
    },
    {
      "title":"Surname",
      "key":"surname"
    },
    {
      "title":"Type",
      "key":"type",
      "filter":"SelectFilter",
      "filterOptions": {
        "Add": "Add",
        "Amend": "Amend",
        "Remove": "Remove"
      }
    }
  ]
}
```

#### Available Options

| Name              | Type     | Description                                                                      |
| ----              | ------   | -----------                                                                      |
| tableID           | string   | Required: An ID for the table.                                                   |
| keyField          | string   | Required: A column key must be selected as the key field.                        |
| tableColumns      | array    | Required: An array of objects with at least a key and title.                     |
| wrapperType       | string   | This string adds a class or classes to the wrapper div around the table.         |
| displayTitle      | string   | This adds a title above the table.                                               |
| defaultSearch     | string   | The default search value.                                                        |
| defaultSort       | array    | The default column to sort by, and if it is asc or desc e.g. ['ref_id', 'desc']. |
| minWidth          | integer  | Define a minimum width for the table.                                            |
| useLocalStorage   | bool     | If true the table filters will be stored using local storage.                    |
| extraToolbarItems | function | A way of passing extra items to the toolbar. [See More](#extra-toolbar-items)    |
| extraButtons      | function | A way of passing extra buttons to the table. [See More](#extra-buttons)          |

##### Using Local Storage

Using local storage will store the column filters and search box values entered as ```tableFilters``` and ```tableSearch```.

LocalStorage can be cleared as below:
```
localStorage.removeItem('tableFilters'); // clear table filters
localStorage.removeItem('tableSearch'); // clear table searches
```

##### Extra Toolbar Items

![Extra Toolbar Options](https://github.com/sean-ww/react-redux-datatable/raw/master/extra-toolbar-options.png)

You can add extra items to the toolbar when you use displayTitle:
```
const ExtraToolbarItem = () =>
    <Link
      class="table-icons"
      to="courses/create-course"
    >
        <span
          class="add-link"
        />
        Add New
    </Link>

const tableSettings = {
    tableID: 'myTable',
    displayTitle: 'Course Catalogue',
    extraToolbarItems: ExtraToolbarItem,
    ...otherSettings,
}
```

##### Extra Buttons

![Extra Buttons](https://github.com/sean-ww/react-redux-datatable/raw/master/extra-buttons.png)

You can add extra buttons to the table using extraButtons:
```
const ExtraButton = () =>
    <Link
      class="table-icons"
      to="courses/create-course"
    >
        <span
          class="add-link"
        />
        Add New
    </Link>

const tableSettings = {
    tableID: 'myTable',
    extraButtons: ExtraButton,
    ...otherSettings,
}
```
