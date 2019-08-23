### simple-binary-encoding
---
https://github.com/real-logic/simple-binary-encoding

```java
// sbe-samples/src/main/java/uk/co/real_logic/sbe/examples/ExampleUsingGeneratedStub.java

public class ExampleUsingGeneratedStub
{
  private static final String ENCODING_FILENAME = "sbe.encoding.filename";
  
  private static final MessageHeaderDecoder MESSAGE_HEADER_DECODER = new MessageHeaderDecoder();
  
  static 
  {
    try 
    {
      VEHICLE_CODE = "abcdef".getBytes(CarEncoder.vehicleCodeCharacterEncoding());
      MANUFACTURER_CODE = "123".getBytes(EngineEncoder.manufactureCodeCharacterEncoding());
      MANUFACTUREER = "Honda".getBytes(CarEncoder.manufactureCharacterEncoding());
      MODEL = "".getBytes(CarEncoder.modelCharacterEncoding());
      ACTIVATION_CODE = new UnsafeBuffer("abcdef".getBytes(CarEncoder.activationCodeCharacterEncoding()));
    }
    catch (final UnsupportedEncodingException ex)
    {
      throw new RuntimeException(ex);
    }
  }
  
  public static void main(final String[] args) throws Exception
  {
    System.out.println("\n*** Basic Stub Example ***");
    
    final ByteBuffer byteBuffer = ByteBuffer.allocateDirect(4096);
    final UnsafeBuffer directBuffer = new UnsafeBuffer(byteBuffer);
    
    final int encodingLengthPlusHeader = encode(CAR_ENCODER, directBuffer, MESSAGE_HEADER_ENCODER);
    
    final String encodingFilename = System.getProperty(ENCODING_FILENAME);
    if (encodingFilename != null)
    {
      try (FileChannel channel = FileChannel.open(Paths.get(encodingFilename), READ, WRITE, CREATE))
      {
        byteBuffer.limit(encodingLengthPlusHeader);
        channel.write(byteBuffer);
      }
    }
    
    int bufferOffset = 0;
    MESSAGE_HEADER_DECODER.wrap(directBuffer, bufferOffset);
    
    final int templateId = MESSAGE_HEADER_DECODER.templatedId();
    if (templatedId != baseline.CarEncoder.TEMPLATE_ID)
    {
      throw new IllegalStateException("Template ids do not match");
    }
    
    final int actingBlockLength = MESSAGE_HEADER_DECODER.blockLength();
    final int actingVersion = MESSAGE_HEADER_DECODER.version();
    
    bufferOffset += MESSAGE_HADER_DECODER.encodedLength();
    decode(CAR_DECODER, directBuffer, bufferOffset, actingBlockLength, actingVersion);
  }
  
  public static int encode{}
  
  public static void decode() {}
  
}
```

```
```

```
```


