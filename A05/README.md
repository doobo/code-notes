# ChatGPT在Java中的使用
主要介绍ChatGPT怎样用Java来调用,并简单的介绍一下OpenAi网站

## 问题回复
通过聊天内容，进行相关的回答
```
public void testChatGPT(){
    OpenAiService service = new OpenAiService(CommonContent.TOKEN);
    CompletionRequest completionRequest = CompletionRequest.builder()
        .prompt("因为我冷漠怎么回复好些")
        .model("text-davinci-003")
        .echo(true)
        .temperature(0.9)	//值在[0,1]之间，越大表示回复越具有不确定性
        .maxTokens(1200)	//回复最大的字符数
        .frequencyPenalty(0.0) //[-2,2]之间，该值越大则更倾向于产生不同的内容
        .presencePenalty(0.0) //[-2,2]之间，该值越大则更倾向于产生不同的内容
        .user(user)
        .build();
        service.createCompletion(completionRequest).getChoices()
            .forEach(OpenAiTests::sayOut);
}
```

## 图片生成
根据输入的描述语言，生成相关的图片
```
public void testImage(){
    OpenAiService service = new OpenAiService(CommonContent.TOKEN);
    CreateImageRequest build = CreateImageRequest.builder()
        .prompt("a white siamese cat")
        .size("256*256")
        .user(user)
        .n(1)
        .build();
    service.createImage(build).getData().forEach(m -> System.out.println(m.getUrl()));
}   
```
* 相关Maven依赖
```xml
<dependency>
    <groupId>com.theokanning.openai-gpt3-java</groupId>
    <artifactId>client</artifactId>
    <version>0.9.0</version>
</dependency>
```