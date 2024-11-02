## JSON Schema Description for Menu JSON

This schema describes the structure of a JSON configuration for a menu, which includes elements such as links, spacers, and nested components. Below is an explanation of the various properties used in the schema:

### Properties:

- **schema**:

    - Type: `string`
    - Format: `uri`
    - Description: The URI reference for the schema. It defines the location of the menu JSON structure.

- **workspace**:

    - Type: `string`
    - Description: A name to indicate the workspace where the menu will be used (e.g., "navbar").

- **elements**:

    - Type: `array`
    - Description: An array containing the individual elements of the menu, such as links or spacers.
    - Items:
        - **component**:
            - Type: `string`
            - Enum: `"link"`, `"spacer"`
            - Description: Specifies the type of element.
        - **text**:
            - Type: `string`
            - Description: The display text for link components.
        - **icon**:
            - Type: `string`
            - Description: Icon class used for the component (e.g., `fa-home`).
        - **type**:
            - Type: `string`
            - Enum: `"href"`, `"menu-item"`
            - Description: Specifies the type of the link (direct link or a menu item).
        - **href**:
            - Type: `string`
            - Description: The hyperlink reference for the link component.
        - **layout**:
            - Type: `string`
            - Description: The layout type that specifies how the link should be presented.
        - **disabled**:
            - Type: `boolean`
            - Description: A flag that indicates whether the link is disabled.
        - **elements**:
            - Type: `array`
            - Description: Nested components under the current element (used for sub-menus).
            - Items: Reference to the same `elements` structure.
        - **permission**:
            - Type: `string`
            - Description: The permission required to view this component.
        - **badge**:
            - Type: `object`
            - Description: Additional badge information for link components (e.g., counter for unread messages).
            - Properties:
                - **component**:
                    - Type: `string`
                    - Enum: `"counter"`
                    - Description: Specifies the badge type.
                - **value**:
                    - Type: `integer`
                    - Description: The value of the badge (e.g., number of notifications).
                - **class**:
                    - Type: `string`
                    - Description: CSS class for badge styling (e.g., "warning").

### Required Properties:

- **schema**: Must be defined.
- **workspace**: Must be defined.
- **elements**: Must be defined.

### Additional Rules:

- **additionalProperties**: `false`
    - Description: No properties other than the specified ones are allowed in any object.

This schema ensures that the menu JSON follows a consistent format, enforcing required properties and validation for nested elements like links, sub-menus, and badges.

