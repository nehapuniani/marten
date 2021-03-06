<!--Title: Custom Projections-->

## Multistream Projections using ViewProjection 
 
The `ViewProjection` class is an implementation of the `IProjection` that can handle building a projection from multiple streams. 
 
This can be setup from configuration like: 
 
<[sample:viewprojection-from-configuration]> 
 
or through a class like: 
 
<[sample:viewprojection-from-class]> 
 
`ProjectEvent` and `DeleteEvent` can operate on events that need a single or multiple Ids operated on. With `ProjectEvent` if a `List<TId>` is passed, the handler method will be called for each Id in the collection. With `DeleteEvent` if a `List<TId>` is passed, then each document tied to the Id in the collection will be removed. Each of these methods take various overloads that allow selecting the Id field implicitly, through a property or through two different Funcs `Func<IDocumentSession, TEvent, TId>` and `Func<TEvent, TId>`. 
 
If additional Marten event details are needed, then events can use the `ProjectionEvent<>` generic when setting them up with `ProjectEvent`. `ProjectionEvent` exposes the Marten Id, Version, Timestamp and Data.