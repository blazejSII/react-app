# react-table-component <!-- .element: class="r-fit-text" -->

[https://github.com/jbetancur/react-data-table-component](https://github.com/jbetancur/react-data-table-component)


## install

```bash[1|2]
npm i react-data-table-component
yarn add react-data-table-component
```


it also needs __styled-components__ installed

```bash[1|2]
npm i react-data-table-component styled-components
yarn add react-data-table-component styled-components
```


<!-- .slide: data-transition="fade-in fade-out" -->
![table workout](./assets/data-table-workout.gif)


## start with component

need a bit of practice

but after some time it starts to be super handy


## minimum code

```html[1,4|2|3]
<DataTable
  columns={[]}
  data={[]}
/>
```


## data

```js[1,6|2|3|4|5]
const data = [
  { id: "asdf-0001", name: "tere fere" },
  { id: "asdf-0003", name: "szuru buru" },
  { id: "asdf-0002", name: "srutu tutu" },
  { id: "asdf-0004", name: "fifi rifi" },
];
```


## columns

```js[1,12|2-5|3|4|6-11|7|8|9|10]
const columns = [
  { 
    name: "name",
    selector: (row) => row.name
  },
  {
    name: "id",
    selector: (row) => row.id,
    sortable: true,
    format: (el) => el.id.toUpperCase()
  },
];
```


## more options

```html[1,8|2|3|4|4-5|6|6-7|10-12]
<DataTable
  columns={columns}
  data={data}
  selectableRows
  onSelectedRowsChange={console.log}
  expandableRows
  expandableRowsComponent={ExpandedComponent}
/>

const ExpandedComponent = ({ data }) => (
  <pre>{JSON.stringify(data, null, 2)}</pre>
);
```


## how it can looks like

![ready table](./assets/data-table-screen-1.png)
