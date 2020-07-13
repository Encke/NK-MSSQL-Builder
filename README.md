# NK-MSSQL-Builder
SQL String Builder Class to Extend NK-MSSQL

## Installation

Install using NPM

```bash
echo "registry=https://npm.pkg.github.com/Encke" >> .npmrc
npm i @encke/nk-mssql-builder --save
```

## How to use

This will allow you to use Mongo like calls to MSSQL Databases with no additional programming.

### Include
```node
const NKSQL = require( '@encke/nk-mssql-builder' )
```

### Get insert query (or queries)

With MSSQL you cannot run a multi insert, so this will return multiple inserts separated by ; so that the full response can be run on the host.

```node
let myQuery = NKSQL.insert( 'users', { username: 'jose', pass: '123', active: false, added: ( new Date() ).getTime() } )
```

### Get update query

```node
let myQuery = NKSQL.update( 'users', { username: 'jose', pass: '123', active: false, added: ( new Date() ).getTime() }, { user_id: 1 } )
```

### Get delete query

```node
let myQuery = NKSQL.delete( 'users', { user_id: 1 } )
```

### Get select queries

```node
let myQuery = NKSQL.query( 'users', 100, { added: -1 }, { user_id: 1 }, [ { from: 'photos', field: 'user_id', fromField: 'user_id', name: 'user_photos' } ] )
```


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
