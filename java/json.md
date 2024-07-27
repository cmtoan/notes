# Json

## Dùng Jackson

### Đọc String thành Json

Đọc String thành Json và chuyển JsonNode thành Object

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

### Viết Json Object thành String

Tạo một ObjectNode, và viết nó thành String
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