# 🔒 Oracle APEX — Mandatory Field Validation (Dynamic Action) -javascript-code

- This script checks that all mandatory fields are filled before running an Insert Process (or any PL/SQL process) in Oracle APEX.
- If any required field is empty, it highlights the missing fields in red and prevents further execution.



# 📜 JavaScript Code
```javaScript

// ✅ Mandatory Field Validation Script for Oracle APEX
// Add this code to a Dynamic Action (on Click of a Button)
// Action Type: Execute JavaScript Code

// List of mandatory fields
var mandatoryItems = [
    'P29_PI_ID',
    'P29_UNIT_ID',
    'P29_LC_TYPE',
    'P29_LC_NO',
    'P29_CUSTOMER_ID',
    'P29_LC_DATE',
    'P29_RECEIVE_DATE',
    'P29_LC_AMOUNT',
    'P29_NEGOTIATING_BANK_ID',
    'P29_ISSUING_BANK_ID',
    'P29_BANK_ID'
];

var allFilled = true;

// Loop through items and check their values
mandatoryItems.forEach(function(item){
    var val = $v(item); // Get page item value
    if(!val || val.trim() === ''){
        allFilled = false;

        // Optional: clear the value
        $s(item, '');

        // Highlight the empty field with a red border
        $('#' + item).css('border', '2px solid red');
    } else {
        // Reset border color if field is filled
        $('#' + item).css('border', '');
    }
});

// If any mandatory field is missing, show alert and stop the process
if(!allFilled){
    alert('⚠️ Please fill all mandatory fields before proceeding!');
    return false; // Stops the next PL/SQL or submit process
}


```

## ⚙️ How to Implement in Oracle APEX

- Go to your page in APEX Builder.

- Create a Dynamic Action on your Save or Submit button.

- Event: Click

- Action 1: Execute JavaScript Code — paste the code above.

- Action 2: Add your PL/SQL Insert Process, and set it to run only if JavaScript validation passes.

- Test the page — empty required fields will now show a red border and stop submission.

 # Thank you
 ## Sanjay Sikder

 You can connect with me on [LinkedIn](https://www.linkedin.com/in/sanjay-sikder/)!
