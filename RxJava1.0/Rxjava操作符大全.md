## Rxjava操作符大全

在Rxjava当中最重要的就是操作符，RxJava当中有着庞大的操作符

### 创建操作符：负责创建Observable对象

| 操作符          | 功能描述                                     |
| ------------ | ---------------------------------------- |
| create()     | 使用一个函数从头创建一个Observable                   |
| just()       | 将一个或多个对象转换成发射这个或这些对象的一个Observable        |
| from()       | 将一个Iterable, 一个Future, 或者一个数组转换成一个Observable |
| repeat()     | 创建一个重复发射指定数据或数据序列的Observable             |
| repeatWhen() | 创建一个重复发射指定数据或数据序列的Observable，它依赖于另一个Observable发射的数据 |
| defer()      | 只有当订阅者订阅才创建Observable；为每个订阅创建一个新的Observable |
| range()      | 创建一个发射指定范围的整数序列的Observable               |
| interval()   | 创建一个按照给定的时间间隔发射整数序列的Observable           |
| timer()      | 创建一个在给定的延时之后发射单个数据的Observable            |
| empty()      | 创建一个什么都不做直接通知完成的Observable               |
| error()      | 创建一个什么都不做直接通知错误的Observable               |
| never()      | 创建一个不发射任何数据的Observable                   |

### 变换操作符：对Observable发射的数据执行变换操作的各种操作符
| 操作符                                      | 功能描述                                     |
| ---------------------------------------- | ---------------------------------------- |
| map()                                    | 对序列的每一项都应用一个函数来变换Observable发射的数据序列       |
| flatMap(), concatMap(), flatMapIterable() | 将Observable发射的数据集合变换为Observables集合，然后将这些Observable发射的数据平坦化的放进一个单独的 |
| switchMap()                              | 将Observable发射的数据集合变换为Observables集合，然后只发射这些Observables最近发射的数据 |
| scan()                                   | 对Observable发射的每一项数据应用一个函数，然后按顺序依次发射每一个值  |
| groupBy()                                | 将Observable分拆为Observable集合，将原始Observable发射的数据按Key分组，每一个Observable发射一组不同的数据 |
| buffer()                                 | 它定期从Observable收集数据到一个集合，然后把这些数据集合打包发射，而不是一次发射一个 |
| window()                                 | 定期将来自Observable的数据分拆成一些Observable窗口，然后发射这些窗口，而不是每次发射一项 |
| cast()                                   | 在发射之前强制将Observable发射的所有数据转换为指定类型         |

### 过滤操作符：用于过滤和选择Observable发射的数据序列

| 操作符                                 | 功能描述                                 |
| ----------------------------------- | ------------------------------------ |
| filter()                            | 过滤数据                                 |
| takeLast()                          | 只发射最后的N项数据                           |
| last()                              | 只发射最后的一项数据                           |
| lastOrDefault()                     | 只发射最后的一项数据，如果Observable为空就发射默认值      |
| takeLastBuffer()                    | 将最后的N项数据当做单个数据发射                     |
| skip()                              | 跳过开始的N项数据                            |
| skipLast()                          | 跳过最后的N项数据                            |
| take()                              | 只发射开始的N项数据                           |
| first() and takeFirst()             | 只发射第一项数据，或者满足某种条件的第一项数据              |
| firstOrDefault()                    | 只发射第一项数据，如果Observable为空就发射默认值        |
| elementAt()                         | 发射第N项数据                              |
| elementAtOrDefault()                | 发射第N项数据，如果Observable数据少于N项就发射默认值     |
| sample() or throttleLast()          | 定期发射Observable最近的数据                  |
| throttleFirst()                     | 定期发射Observable发射的第一项数据               |
| throttleWithTimeout() or debounce() | 只有当Observable在指定的时间后还没有发射数据时，才发射一个数据 |
| timeout()                           | 如果在一个指定的时间段后还没发射数据，就发射一个异常           |
| distinct()                          | 过滤掉重复数据                              |
| distinctUntilChanged()              | 过滤掉连续重复的数据                           |
| ofType()                            | 只发射指定类型的数据                           |
| ignoreElements()                    | 丢弃所有的正常数据，只发射错误或完成通知                 |

### 结合操作符：用于组合多个Observables的组合使用

| 操作符                       | 功能描述                                     |
| ------------------------- | ---------------------------------------- |
| startWith()               | 在数据序列的开头增加一项数据                           |
| merge()                   | 将多个Observable合并为一个                       |
| mergeDelayError()         | 合并多个Observables，让没有错误的Observable都完成后再发射错误通知 |
| zip()                     | 使用一个函数组合多个Observable发射的数据集合，然后再发射这个结果    |
| and(), then(), and when() | (rxjava-joins) 通过模式和计划组合多个Observables发射的数据集合 |
| combineLatest()           | 当两个Observables中的任何一个发射了一个数据时，通过一个指定的函数组合每个Observable发射的最新数据（一共两个数据），然后发射这个函数的结果 |
| join() and groupJoin()    | 无论何时，如果一个Observable发射了一个数据项，只要在另一个Observable发射的数据项定义的时间窗口内，就将两个Observable发射的数据合并发射 |
| switchOnNext()            | 将一个发射Observables的Observable转换成另一个Observable，后者发射这些Observables最近发射的数据 |

### 辅助操作符：用于bservable的辅助操作符

| 操作符                                | 功能描述                                     |
| ---------------------------------- | ---------------------------------------- |
| materialize()                      | 将Observable转换成一个通知列表convert an Observable into a list of Notifications |
| dematerialize()                    | 将上面的结果逆转回一个Observable                    |
| timestamp()                        | 给Observable发射的每个数据项添加一个时间戳               |
| serialize()                        | 强制Observable按次序发射数据并且要求功能是完好的            |
| cache()                            | 记住Observable发射的数据序列并发射相同的数据序列给后续的订阅者     |
| observeOn()                        | 指定观察者观察Observable的调度器                    |
| subscribeOn()                      | 指定Observable执行任务的调度器                     |
| doOnEach()                         | 注册一个动作，对Observable发射的每个数据项使用             |
| doOnCompleted()                    | 注册一个动作，对正常完成的Observable使用                |
| doOnError()                        | 注册一个动作，对发生错误的Observable使用                |
| doOnTerminate()                    | 注册一个动作，对完成的Observable使用，无论是否发生错误         |
| doOnSubscribe()                    | 注册一个动作，在观察者订阅时使用                         |
| doOnUnsubscribe()                  | 注册一个动作，在观察者取消订阅时使用                       |
| finallyDo()                        | 注册一个动作，在Observable完成时使用                  |
| delay()                            | 延时发射Observable的结果                        |
| delaySubscription()                | 延时处理订阅请求                                 |
| timeInterval()                     | 定期发射数据                                   |
| using()                            | 创建一个只在Observable生命周期存在的资源                |
| single()                           | 强制返回单个数据，否则抛出异常                          |
| singleOrDefault()                  | 如果Observable完成时返回了单个数据，就返回它，否则返回默认数据     |
| toFuture(), toIterable(), toList() | 将Observable转换为其它对象或数据结构                  |