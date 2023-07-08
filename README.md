# International Telephone Input for Angular Material (ngxMatTelInput)
An Angular Material package for entering and validating international telephone numbers. It adds a flag dropdown to any input, detects the user's country, displays a relevant placeholder and provides formatting/validation methods.

## Caution
This is a fork from the [ngx-mat-intl-tel-input](https://github.com/tanansatpal/ngx-mat-intl-tel-input) library whish does not seems to be maintained anymore. _Last commit is over a year_

**Supports:**

- Angular >=15
- Angular Material >=15
- ReactiveFormsModule
- FormsModule
- Validation with [libphonenumber-js](https://github.com/catamphetamine/libphonenumber-js)

## Installation

### Install Dependencies

`$ npm i libphonenumber-js@latest`

### Install This Library

`$ npm i ngx-mat-tel-input@latest`

## Usage

### Import

Add `NgxMatTelInputComponent` to your component file:

```ts
imports: [NgxMatTelInputComponent];
```

## Example

Refer to main app in this repository for working example.

```html
<form #f="ngForm" [formGroup]="phoneForm">
  <ngx-mat-tel-input
    [preferredCountries]="['us', 'gb']"
    [enablePlaceholder]="true"
    [enableSearch]="true"
    name="phone"
    describedBy="phoneInput"
    formControlName="phone"
  ></ngx-mat-tel-input>
</form>
```

```html

<form #f="ngForm" [formGroup]="phoneForm">
  <ngx-mat-tel-input
  [preferredCountries]="['us', 'gb']"
  [enablePlaceholder]="true"
  [enableSearch]="true"
  name="phone"
  autocomplete="tel"
  (countryChanged)="yourComponentMethodToTreatyCountryChangedEvent($event)" // $event is a instance of current select Country
  formControlName="phone"></ngx-mat-tel-input>
</form>

```

If you want to show the sample number for the country selected or errors , use mat-hint anf mat-error as

```html
<form #f="ngForm" [formGroup]="phoneForm">
  <ngx-mat-tel-input
    [preferredCountries]="['us', 'gb']"
    [onlyCountries]="['us', 'gb', 'es']"
    [enablePlaceholder]="true"
    name="phone"
    autocomplete="tel"
    formControlName="phone"
    #phone
  ></ngx-mat-tel-input>
  <mat-hint>e.g. {{phone.selectedCountry.placeHolder}}</mat-hint>
  <mat-error *ngIf="f.form.controls['phone']?.errors?.required"
    >Required Field</mat-error
  >
  <mat-error *ngIf="f.form.controls['phone']?.errors?.validatePhoneNumber"
    >Invalid Number</mat-error
  >
</form>
```

## Options

| Options            | Type       | Default     | Description                                                                         |
| ------------------ | ---------- | ----------- | ----------------------------------------------------------------------------------- | --- |
| preferredCountries | `string[]` | `[]`        | List of country abbreviations, which will appear at the top.                        |
| onlyCountries      | `string[]` | `[]`        | List of manually selected country abbreviations, which will appear in the dropdown. |     |
| inputPlaceholder   | `string`   | `undefined` | Placeholder for the input component.                                                |
| enablePlaceholder  | `boolean`  | `true`      | Input placeholder text, which adapts to the country selected.                       |
| enableSearch       | `boolean`  | `false`     | Whether to display a search bar to help filter down the list of countries           |
| format             | `string`   | `default`   | Format of "as you type" input. Possible values: national, international, default    |
| describedBy        | `string`   | `undefined` | Use aria-described by with the input field                                          |

## Css variable
| Name                       | Default | Explanation                                         |
| -------------------------- | ------- | --------------------------------------------------- |
| `--ngxMatTelInput-color`   | `#000`  | If you wish to change the overall color             |
| `--ngxMatTelInput-opacity` | `0`     | If you wish the country flag to be shown by default |

## Library Contributions

- Fork repo.
- Go to `./projects/ngx-mat-tel-input`
- Update `./src/lib` with new functionality.
- Update README.md
- Pull request.

### Helpful commands

- Build lib: `$ npm run build_lib`
- Copy license and readme files: `$ npm run copy-files`
- Create package: `$ npm run npm_pack`
- Build lib and create package: `$ npm run package`

### Use locally

After building and creating package, you can use it locally too.

In your project run:

`$ npm install --save {{path to your local '*.tgz' package file}}`

### Acknowledgments
This repo is a fork from the [ngx-mat-intl-tel-input](https://github.com/tanansatpal/ngx-mat-intl-tel-input) library.
