# universal-domain
This package is an "ORM Solution" on Java, that simplifies DB operations  
and provides strong support for API and system development.

This is also used in the BRMS Package "universal-rules".

<img src="https://camo.qiitausercontent.com/00f9cc65cdea735164a23edab49f10a1bf9cb56a/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f2d4a6176612d3030373339362e7376673f6c6f676f3d6a617661267374796c653d666f722d7468652d6261646765">

## development images

### creating an entity
```
import jp.co.cam.universal.appl.domain.DomainHandler;
import jp.co.cam.universal.appl.domain.entity.impl.EntityObject;

public class UserEntity
    extends EntityObject
{
    public UserEntity()
    {
        // Parameters : 1.DB Connection, 2.Table name
        super(DomainHandler.getConnection("default", "current"), "USER");
    }
}
```

### creating a process to get one row
```
// User Entity
UserEntity user = new UserEntity();
			
// Search conditions
FilterIF where = user.getFilter();
where.add("USER_ID", "123");

// One row of data that matches the set conditions has been persisted
user.fill();
```

### creating a process to get rows
```
// User Entity
UserEntity user = new UserEntity();
			
// Search conditions
FilterIF where = user.getFilter();
where.addLike("USER_NAME", "HIFUMI");
where.nextEntry();
where.addLike("USER_NAME", "SATOMI");

// Rows of data that are not persisted
EntitySetIF resultList = user.find();

while (resultList.next())
{
    // One row of data that matches the set conditions has been persisted
    EntityObjectIF result = resultList.get();
}
```

### creating a process to add data
```
// User Entity
UserEntity user = new UserEntity();

// Set contents
user.setString("USER_ID",   "313");
user.setString("USER_NAME", "MISOSAZAI SATOMI");

user.insert();
```

### creating a process to update datas
```
// User Entity
UserEntity user = new UserEntity();
			
// Set update conditions
FilterIF where = user.getFilter();
where.add("USER_ID", "313");

// Set update contents
user.setString("PASSWORD", "CAC");

user.update();
```

### creating a process to delete datas
```
// User Entity
UserEntity user = new UserEntity();
			
// Set delete conditions
FilterIF where = user.getFilter();
where.add("USER_ID", "313");

user.delete();
```

others
* You can create entities that execute customized SQL.
* We can handle BLOB and CLOB data.
* We can manage multiple DB connections and multiple separate transactions.
* When you want to expand any processing, we're designed to make it easy.

## dependencies
"universal-commons"

## for License
The source code is licensed MIT, please see "LICENSE" file.

Special Thanks [The MIT License](https://opensource.org/license/mit/)
