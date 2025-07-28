# NIC Validation System

A comprehensive web-based National Identity Card (NIC) validation system that supports both old and new NIC formats, calculates date of birth, determines gender, and validates birth dates.

## Features

- **Dual Format Support**: Validates both old (10 digits + V) and new (12 digits) NIC formats
- **Date of Birth Calculation**: Accurately calculates birth date using leap year logic
- **Gender Detection**: Determines gender based on day number patterns
- **Format Conversion**: Converts between old and new NIC formats
- **Future Date Validation**: Prevents NICs with future birth dates
- **Existing User Check**: Alerts for NICs already in the system
- **Responsive Design**: Works on desktop and mobile devices

## NIC Format Rules

### Old NIC Format (10 digits + V)
- **Format**: `YYDDDSSSSV`
- **YY**: Birth year (last 2 digits)
- **DDD**: Day of year + gender indicator
  - ≤ 500: Male, actual day = the number
  - > 500: Female, actual day = number - 500 (standard year) or number - 501 (leap year)
- **SSSS**: Serial number
- **V**: Check digit

### New NIC Format (12 digits)
- **Format**: `YYYYDDDSSSSS`
- **YYYY**: Full birth year
- **DDD**: Day of year + gender indicator
  - ≤ 500: Male, actual day = the number
  - > 500: Female, actual day = number - 500 (standard year) or number - 501 (leap year)
- **SSSSS**: Serial number

## Installation & Setup

### Step 1: Download Files
1. Download the following files to your computer:
   - `base.html`
   - `style.css`

### Step 2: Create Project Folder
1. Create a new folder on your computer (e.g., "NIC Validation System")
2. Place both files in this folder

### Step 3: Open the Application
1. Double-click on `base.html` to open it in your web browser
2. The application will load automatically

## How to Use

### Step 1: Enter NIC Number
1. In the input field, enter a NIC number in either format:
   - **Old Format**: `901234567V` (9 digits + V)
   - **New Format**: `199012345678` (12 digits)

### Step 2: Validate NIC
1. Click the "Check NIC" button
2. Or press Enter key while in the input field

### Step 3: View Results
The system will display:
- **NIC Type**: Old NIC or New NIC
- **Date of Birth**: Calculated birth date
- **Gender**: Male or Female
- **Year Type**: Leap Year or Standard Year
- **Converted NIC**: The other format version

### Step 4: Check for Existing Users
- If the NIC belongs to an existing user, an alert will appear
- Sample existing NICs for testing:
  - `901234567V`
  - `199012345678`
  - `881234567V`
  - `198812345678`

## Validation Rules

### Format Validation
- **Old NIC**: Must be exactly 9 digits + V
- **New NIC**: Must be exactly 12 digits
- Only numbers and 'V' are allowed

### Date Validation
- Birth date cannot be in the future
- Day number must be valid for the year type
- Standard year: 1-365 days
- Leap year: 1-366 days

### Gender Calculation
- **Male**: Day number ≤ 500
- **Female**: Day number > 500

### DOB Calculation
- **Male**: Use actual day number
- **Female (Standard Year)**: Subtract 501 from day number
- **Female (Leap Year)**: Subtract 500 from day number

## Examples

### Valid Old NIC Examples
```
901234567V → Male, May 3, 1990
907345678V → Female, August 22, 1990
881234567V → Male, May 2, 1988
```

### Valid New NIC Examples
```
199012345678 → Male, May 3, 1990
199073456789 → Female, August 22, 1990
198812345678 → Male, May 2, 1988
```

### Invalid Examples
```
901234567 → Missing V
9012345678V → Wrong length
19901234567 → Too short
1990123456789 → Too long
203012345678 → Future date
```

## Technical Details

### Leap Year Detection
A year is a leap year if:
- It's divisible by 4 AND not divisible by 100, OR
- It's divisible by 400

### DOB Calculation Algorithm
1. Extract year and day from NIC
2. Determine gender from day number
3. Adjust day number for females based on year type
4. Calculate date using JavaScript Date object
5. Validate against current date

### Error Handling
- Format validation errors
- Future date validation
- Invalid day number validation
- Existing user alerts

## Browser Compatibility

- **Chrome**: ✅ Fully supported
- **Firefox**: ✅ Fully supported
- **Safari**: ✅ Fully supported
- **Edge**: ✅ Fully supported
- **Internet Explorer**: ⚠️ Limited support

## File Structure

```
NIC Validation System/
├── base.html          # Main HTML file with JavaScript logic
├── style.css          # CSS styling file
└── README.md          # This documentation file
```

## Troubleshooting

### Common Issues

1. **File won't open**
   - Ensure both files are in the same folder
   - Check file permissions
   - Try opening with a different browser

2. **Validation not working**
   - Check NIC format (exact number of digits)
   - Ensure 'V' is included for old format
   - Verify no spaces or special characters

3. **Future date errors**
   - NIC birth date cannot be after current date
   - Check year in NIC number

4. **Styling issues**
   - Ensure `style.css` is in the same folder as `base.html`
   - Check browser console for errors

## Testing

### Test Cases
1. **Valid Old NICs**:
   - `901234567V`
   - `881234567V`
   - `951234567V`

2. **Valid New NICs**:
   - `199012345678`
   - `198812345678`
   - `199512345678`

3. **Invalid NICs**:
   - `901234567` (missing V)
   - `19901234567` (too short)
   - `203012345678` (future date)

## Support

For issues or questions:
1. Check the troubleshooting section above
2. Verify file structure and permissions
3. Test with different browsers
4. Ensure all files are present and properly named

## Version History

- **v1.0**: Initial release with basic validation
- **v1.1**: Added leap year logic and gender-specific calculations
- **v1.2**: Added future date validation and existing user checks
- **v1.3**: Enhanced error messages and responsive design

---

**Note**: This system is designed for educational and demonstration purposes. For production use, additional security measures and server-side validation should be implemented. 