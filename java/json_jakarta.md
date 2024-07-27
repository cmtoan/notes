# Json với Jakarta

````Java
import jakarta.json.*;
import jakarta.json.bind.Jsonb;
import jakarta.json.bind.JsonbBuilder;
import jakarta.json.stream.JsonGenerator;
````

## Viết Object thành Json

Viết Java Object thành Json
````Java
    void writeMessage() throws FileNotFoundException {
        Message message = new Message("Hello World");
        Jsonb jsonBuilder = JsonbBuilder.create();
        jsonBuilder.toJson(message, new FileOutputStream("./hello.json"));
        System.out.println(jsonBuilder.toJson(message));
    }
    public record Message(String value) {}
````

Tạo một JsonObject, và viết nó thành Json
````Java
void writeJson() {
    String text = """
            query String {
                value : "123"
            }
            """;
    JsonObject jsonObject = Json.createObjectBuilder()
            .add("query", text)
            .build();

    System.out.println(jsonObject.toString());

    StringWriter stringWriter = new StringWriter();
    try (JsonWriter jsonWriter = Json.createWriterFactory(Collections.singletonMap(JsonGenerator.PRETTY_PRINTING, true))
            .createWriter(stringWriter)) {
        jsonWriter.writeObject(jsonObject);
    }
    System.out.println(stringWriter);
}
````

## Đọc Json thành Object

Đọc Json thành Java Object
````Java
void readMessage() throws FileNotFoundException {
    String json = """
            {"value":"Hello World"}
            """;
    Jsonb jsonBuilder = JsonbBuilder.create();
    Message message = jsonBuilder.fromJson(new FileInputStream("./hello.json"), Message.class);
    System.out.println(message);
    System.out.println(jsonBuilder.fromJson(json, Message.class));
}
````

Đọc Json thành JsonObject/JsonStructure
````Java
    void readToJsonNode() {
        String json = """
                {"value":"Hello World"}
                """;
        JsonReader jsonReader = Json.createReader(new StringReader(json));
//        JsonStructure jsonStructure = jsonReader.read();
//        System.out.println(jsonStructure.getValue("/value"));
        JsonObject jsonObject = jsonReader.readObject();
        System.out.println(jsonObject.getJsonString("value"));
    }
````

Đọc Json thành JsonObject và chuyển JsonObject thành Java Object
````Java
    void readJson() {
        String json = """
                {
                  "data": {
                    "result": {
                      "value": "Hello World"
                    }
                  }
                }
                """;

        JsonObject jsonObject = Json.createReader(new StringReader(json))
                .readObject();
        JsonObject data = jsonObject.getJsonObject("data");
        System.out.println("data = " + data);

        Jsonb jsonBuilder = JsonbBuilder.create();
        Result result = jsonBuilder.fromJson(data.toString(), Result.class);
        System.out.println(result);
    }

    public record Result(Value result) {}
    public record Value(String value) {}
````

Đọc Json Array String thành Java List
````Java
    void readToList() {
        String json = """
                [{"value":"Hello World"}, {"value":"Hello Everybody"}]
                """;
        JsonArray jsonArray = Json.createReader(new StringReader(json))
                .readArray();

        List<Message> messages = new ArrayList<>();
        Jsonb jsonBuilder = JsonbBuilder.create();

        for (JsonValue jsonValue : jsonArray) {
            messages.add(jsonBuilder.fromJson(jsonValue.toString(), Message.class));
        }
        System.out.println(messages);
    }
````

