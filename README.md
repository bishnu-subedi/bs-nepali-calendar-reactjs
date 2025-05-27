# bs-nepali-calendar-reactjs

[![NPM Version](https://img.shields.io/npm/v/bs-nepali-calendar-reactjs.svg)](https://www.npmjs.com/package/bs-nepali-calendar-reactjs)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

`bs-nepali-calendar-reactjs` is a simple and reusable Nepali datepicker component for ReactJS. It supports both Nepali and English languages, multiple themes, and customizable date formats.

## Features

- **Language Support**: Nepali (`ne`) and English (`en`).
- **Customizable Themes**: Default, Red, Green, Blue, Dark, and Deep Dark.
- **Date Format Options**: Flexible date formatting options for both Nepali and English.
- **Min/Max Date Support**: Restrict date selection within a range.
- **Lightweight**: Built with ReactJS and optimized for performance.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
  - [Class Component Example](#class-component-example)
  - [Functional Component Example](#functional-component-example)
  - [Using the `adToBs` Method](#using-the-adtobs-method)
- [Props](#props)
- [Themes](#themes)
- [Date Format](#date-format)
- [License](#license)

## Installation

Install the package via npm or yarn:

```bash
npm install bs-nepali-calendar-reactjs
```

or

```bash
yarn add bs-nepali-calendar-reactjs
```

## Usage

### Class Component Example

```jsx
import React from 'react';
import Calendar from 'bs-nepali-calendar-reactjs';
import 'bs-nepali-calendar-reactjs/dist/index.css';

class App extends React.Component {
  state = { date: '' };

  onChange = ({ bsDate, adDate }) => {
    console.log('Selected Date:', bsDate, adDate);
    this.setState({ date: bsDate });
  };

  render() {
    return (
      <div>
        <Calendar
          onChange={this.onChange}
          language="ne"
          theme="default"
          dateFormat="YYYY-MM-DD"
        />
      </div>
    );
  }
}

export default App;
```

### Functional Component Example

```jsx
import React, { useState } from 'react';
import Calendar from 'bs-nepali-calendar-reactjs';
import 'bs-nepali-calendar-reactjs/dist/index.css';

function App() {
  const [date, setDate] = useState('');

  const handleDateChange = ({ bsDate, adDate }) => {
    console.log('Selected Date:', bsDate, adDate);
    setDate(bsDate);
  };

  return (
    <div>
      <Calendar
        onChange={handleDateChange}
        language="en"
        theme="red"
        dateFormat="DDDD, MMMM DD, YYYY"
      />
    </div>
  );
}

export default App;
```

### Using the `adToBs` and `adToBsForDate` Methods

The `adToBs` method allows you to convert an English (AD) date to a Nepali (BS) date programmatically. Here's how to use it:

```javascript
import { adToBs } from 'bs-nepali-calendar-reactjs';

const englishDate = '2023-05-25'; // Example AD date
const nepaliDate = adToBs(englishDate);

console.log('Converted Nepali Date:', nepaliDate);
// Output: { currentYear: 2080, currentMonth: 2, currentDay: 11 }
```

The `adToBsForDate` method converts an AD date to a formatted BS date string. Here's an example:

```javascript
import { adToBsForDate } from 'bs-nepali-calendar-reactjs';

const englishDate = '2023-05-25'; // Example AD date
const formattedNepaliDate = adToBsForDate(englishDate, 'YYYY-MM-DD');

console.log('Formatted Nepali Date:', formattedNepaliDate);
// Output: '2080-02-11'
```

This method is useful for scenarios where you need a formatted BS date string directly.

## Props

| Prop Name       | Description                                                                 | Default Value | Example Values                          |
|------------------|-----------------------------------------------------------------------------|---------------|-----------------------------------------|
| `className`      | Custom class for the input field.                                          | `''`          | `'form-control'`                        |
| `dateFormat`     | Format for the displayed date.                                             | `'YYYY-MM-DD'`| `'DDDD, MMMM DD, YYYY'`                |
| `language`       | Language for the calendar (`ne` for Nepali, `en` for English).            | `'ne'`        | `'en'`, `'ne'`                          |
| `onChange`       | Callback function triggered when a date is selected.                      | `undefined`   | `(value) => console.log(value)`         |
| `style`          | Inline styles for the input field.                                        | `{}`          | `{{ color: 'red' }}`                    |
| `theme`          | Theme for the calendar.                                                   | `'default'`   | `'red'`, `'blue'`, `'green'`, `'dark'`  |
| `minDate`        | Minimum selectable date in BS format.                                     | `''`          | `'2077-01-01'`                          |
| `maxDate`        | Maximum selectable date in BS format.                                     | `''`          | `'2077-12-30'`                          |
| `defaultDate`    | Default selected date in BS format.                                       | `''`          | `'2077-05-15'`                          |
| `hideDefaultValue`| Hides the default value in the input field.                              | `false`       | `true`, `false`                         |

## Themes

The following themes are supported:

- `default`
- `red`
- `green`
- `blue`
- `dark`
- `deepdark`

To apply a theme, pass the `theme` prop to the `Calendar` component:

```jsx
<Calendar theme="blue" />
```

## Date Format

The `dateFormat` prop allows you to customize the format of the displayed date. Supported format tokens:

- `YYYY`: Full year (e.g., `2077`).
- `YY`: Last two digits of the year (e.g., `77`).
- `MMMM`: Full month name (e.g., `Baishakh`).
- `MM`: Month number with leading zero (e.g., `01`).
- `M`: Month number without leading zero (e.g., `1`).
- `DDDD`: Full day name (e.g., `Sunday`).
- `DDD`: Short day name (e.g., `Sun`).
- `DD`: Day of the month with leading zero (e.g., `01`).
- `D`: Day of the month without leading zero (e.g., `1`).

### Example

```jsx
<Calendar dateFormat="DDDD, MMMM DD, YYYY" />
```

Output: `Sunday, Baishakh 01, 2077`

## License

This project is licensed under the [MIT License](LICENSE).

---

For more details, visit the [GitHub repository](https://github.com/bishnu-subedi/bs-nepali-calendar-reactjs).
