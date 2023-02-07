# 很好用的一种公共体
主要介绍这几年编码工作中，用得最多的一种返回体

## 使用方法
请求体继承PageBaseQuery，自带分页和排序；
返回体使用ResultTemplate包装，有公共的出数
返回过程中，使用ResultUtils免去频繁新建对象

## 一种Builder方法
```
UnionCacheRequest request = SimpleBuilder.of(UnionCacheRequest::new)
    .with(UnionCacheRequest::setMethod, method)
    .with(UnionCacheRequest::setRCache, cache)
    .with(UnionCacheRequest::setKey, redisKey)
    .with(UnionCacheRequest::setExpire, cache.expiredTime())
    .build();
```