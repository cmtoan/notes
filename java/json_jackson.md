# Json với Jackson

## Dùng Jackson Maven

````
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.17.2</version>
</dependency>
````

## Viết Object thành Json

Viết Java Object thành Json
````Java
    void writeMessage() throws IOException {
        record Message(String value) {}
        Message message = new Message("Hello World");
        objectMapper.writeValue(new File("./message.json"), message);
        System.out.println(objectMapper.writeValueAsString(message));
        System.out.println(objectMapper.writerWithDefaultPrettyPrinter().writeValueAsString(message));
    }
````

Tạo một ObjectNode, và viết nó thành Json
````Java
    void writeJson() throws JsonProcessingException {
        ObjectNode root = objectMapper.createObjectNode();
        String text = """
                query String {
                    value : "123"
                }
                """;
        root.put("query", text);
        System.out.println(objectMapper.writeValueAsString(root));
    }
````

## Đọc Json thành Object

Đọc Json thành Java Object
````Java
    void readMessage() throws IOException {
        record Message(String value) {}
        Message message = objectMapper.readValue(new File("./message.json"), Message.class);
        System.out.println(message);
        String json = """
                {"value":"Hello World"}
                """;
        message = objectMapper.readValue(json, Message.class);
        System.out.println(message);
    }
````

Đọc Json thành JsonNode
````Java
    void readToJsonNode() throws IOException {
        String json = """
                {"value":"Hello World"}
                """;
        JsonNode jsonNode = objectMapper.readTree(json);
        System.out.println(jsonNode.get("value"));
    }
````

Đọc Json thành JsonNode và chuyển JsonNode thành Java Object

````Java
    void readJson() throws JsonProcessingException {
        ObjectMapper objectMapper = new ObjectMapper();
        String json = """
                {
                  "data": {
                    "result": {
                      "value": "Hello World"
                    }
                  }
                }
                """;
        JsonNode jsonNode = objectMapper.readTree(json);
        JsonNode data = jsonNode.get("data");
        System.out.println("data = " + data);

        Result result = objectMapper.treeToValue(data, Result.class);
        System.out.println("result = " + result);
    }

    record Result(Value result) {}

    record Value(String value) {}
````

Đọc Json Array String thành Java List

````Java
    void readToList() throws IOException {
        record Message(String value) {}
        String json = """
                [{"value":"Hello World"}, {"value":"Hello Everybody"}]
                """;
        List<Message> messages = objectMapper.readValue(json, new TypeReference<>() {});
        System.out.println(messages);
    }
````

Đọc Json thành Java Map

````Java
    void readToMap() throws IOException {
        String json = """
                {
                  "data": {
                    "result": {
                      "value": "Hello World"
                    }
                  },
                  "metadata": {
                    "information": "message"
                  }
                }
                """;
        Map<String, Object> map = objectMapper.readValue(json, new TypeReference<>() {});
        System.out.println(map);
    }
````