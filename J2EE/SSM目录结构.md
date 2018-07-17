| 文件名    | 作用                                                         |
| --------- | ------------------------------------------------------------ |
| src       | 根目录，没什么好说的，下面有 main 和 test。                  |
| main      | 主要目录，可以放 java 代码和一些资源文件。                   |
| java      | 存放我们的 java 代码，这个文件夹要使用 Build Path -> Use as Source Folder，这样看包结构会方便很多，新建的包就相当于在这里新建文件夹咯。 |
| resources | 存放资源文件，譬如各种的 spring，mybatis，log 配置文件。     |
| mapper    | 存放 dao 中每个方法对应的 sql，在这里配置，无需写 daoImpl。  |
| spring    | 这里当然是存放 spring 相关的配置文件，有 dao service web三层。 |
| sql       | 其实这个可以没有，但是为了项目完整性还是加上吧。             |
| webapp    | 这个貌似是最熟悉的目录了，用来存放我们前端的静态资源，如jsp js css。 |
| resources | 这里的资源是指项目的静态资源，如js css images等。            |
| WEB-INF   | 很重要的一个目录，外部浏览器无法访问，只有项目内部才能访问，可以把 jsp 放在这里，另外就是web.xml 了。你可能有疑问了，为什么上面java中的 resources 里面的配置文件不妨在这里，那么是不是会被外部窃取到？你想太多了，部署时候基本上只有 webapp 里的会直接输出到根目录，其他都会放入WEB-INF里面，项目内部依然可以使用 classpath:XXX 来访问，好像IDE里可以设置部署输出目录，这里扯远了~ |
| test      | 这里是测试分支。                                             |
| java      | 测试 java 代码，应遵循包名相同的原则，这个文件夹同样要使用 Build Path -> Use as Source Folder，这样看包结构会方便很多。 |
| resources | 没什么好说的，好像也很少用到，但这个是 maven 的规范。        |