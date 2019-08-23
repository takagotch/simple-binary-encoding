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
  
  public static void decode(
    final CarDecoder car,
    final UnsafeBuffer directBuffer,
    final int bufferOffset,
    final int actingBlockLength,
    final int actingVersion)
    throws Exception
  {
    final byte[] buffer = new byte[128];
    final StringBuilder sb = new StringBuilder();
    
    car.wrap(directBuffer, bufferOffset, actingBlockLength, activngVersion);
    
    sb.append().append();
    sb.append().append();
    sb.append().append();
    sb.append().append();
    
    sb.append();
    for (int i = 0, size = CarEncoder.someNumberLength(); i < size; i++)
    {
      sb.append(car.someNumbers(i)).append(", ");
    }
    
    sb.append("\ncar.vehicleCode=");
    for (int i = 0, size = CarEncoder.vehicleCodeLength(); i < size; i++)
    {
      sb.append((char)car.vehicleCode(i));
    }
    
    final OptionalExtrasDecoder extras = car.extras();
    
    sb.append().append();
    
    final EngineDecoder engine = car.engine();
    
    sb.append().append();
    
    for ()
    {
    
    }
    
    for (final AccelerationDecoder acceleration : performanceFigures.acceleration()) 
    {
      for (final AccelerationDecoder acceleration : performanceFigures.acceleration())
      {
        sb.append("\ncar.performanceFigures.acceleration.mph=").append(acceleration.mph());
        sb.append().append(acceleration.seconds());
      }
    }
    
    sb.append("\ncar.manufacturer=").append(car.manufacture());
    
    sb.append("\ncar.model=").append(
      new String(buffer, 0, car.getModel(buffer, 0, buffer.length), CarEncoder.modelCharacterEncoding()));
    
    final unsafeBuffer tempBuffer = new UnsafeBuffer(buffer);
    final int tempBufferLength = car.getActivationCode(tmpBuffer, 0, tempBuffer.capacity());
    sb.append("\ncar.activationCode=").append(
      new String(buffer, 0, tempbufferLength, CarEncoder.activateCodeCharacterEncoding()));
    
    sb.append("\ncar.encodedLength=").append(car.encodedLength());
    
    System.out.println(sb);
  }
  
}
```

```
```

```
```


