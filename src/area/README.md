# Area

### Intro

The Picker component is usually used with [Popup](#/en-US/popup) Component.

### Install

``` javascript
import Vue from 'vue';
import { Area } from 'vant';

Vue.use(Area);
```

## Usage

### Basic Usage

To initailize `Area` component, `area-list` property is required. Data structure will be introduced later. 

```html
<van-area :area-list="areaList" />
```

### Initial Value

To have a selected value，simply pass the `code` of target area to `value` property.

```html
<van-area :area-list="areaList" value="110101" />
```

### Columns Number

`columns-num` property is used to config number of columns to be displayed. This component has 3 columns corresponding to a 3 level picker by default.
Set `columns-num` with 2, you'll have a 2 level picker.

```html
<van-area :area-list="areaList" :columns-num="2" title="Title" />
```

### Columns Placeholder

`columns-placeholder` property is used to config placeholder of columns.

```html
<van-area
  :area-list="areaList"
  :columns-placeholder="['Choose', 'Choose', 'Choose']"
  title="Title"
/>
```

## API

### Props

| Attribute | Description | Type | Default |
|------|------|------|------|
| value | the `code` of selected area | *string* | - |
| title | Toolbar title | *string* | - |
| area-list | Area data | *object* | - |
| columns-num | level of picker | *string \| number* | `3` |
| columns-placeholder `v2.2.5` | placeholder of columns | *string[]* | `[]` |
| item-height | Option height | *number* | `44` |
| loading | Whether to show loading prompt | *boolean* | `false` |
| visible-item-count | Count of visible columns | *number* | `5` |
| confirm-button-text | Text of confirm button | *string* | `Confirm` |
| cancel-button-text | Text of cancel button | *string* | `Cancel` |
| is-oversea-code `v2.1.4` | The method to validate oversea code | *() => boolean* | - |
| swipe-duration `v2.2.13` | Duration of the momentum animation，unit `ms` | *number*  | `1000` |

### Events

| Event | Description | Arguments |
|------|------|------|
| confirm | triggers when clicking the confirm button | an array |
| cancel | triggers when clicking the cancel button | - |
| change | Triggered when current option changed | Picker instance, current values，column index |

### Methods

Use [ref](https://vuejs.org/v2/api/#ref) to get Area instance and call instance methods

| Name | Description | Attribute | Return value |
|------|------|------|------|
| reset | Reset all options by code | code?: string | - |

### areaList Data Structure

An object contains three properties: `province_list`, `city_list` and `county_list`. 
Each property is a simple key-value object, key is a 6-bit code of the area of which first two bits stand for the province or state, middle two bits are used as city code and the last two are district code, value is the name of the area. If the code stands for an area that has sub-areas, lower bits of it will be filled with 0.

Example of `AreaList`

```js
{
  province_list: {
    110000: 'Beijing',
    330000: 'Zhejiang Province'
  },
  city_list: {
    110100: 'Beijing City',
    330100: 'Hangzhou',
  },
  county_list: {
    110101: 'Dongcheng District',
    110102: 'Xicheng District',
    110105: 'Chaoyang District',
    110106: 'Fengtai District'
    330105: 'Gongshu District',
    330106: 'Xihu District',
    // ....
  }
}
```

All code of China: [Area.json](https://github.com/youzan/vant/blob/dev/src/area/demo/area-en.js)

### argument of callback function confirm

An array contains selected area objects.

`code` - code of selected area, `name` - name of selected area
```js
[{
  code: '330000',
  name: 'Zhejiang Province'
}, {
  code: '330100',
  name: 'Hangzhou'
},{
  code: '330105',
  name: 'Xihu District'
}]
```
