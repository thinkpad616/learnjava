# Java I/O and NIO/NIO.2 (Study Guide + Examples)

## Contents
- java.io streams (byte/char)
- Readers/Writers
- Buffering
- Serialization vs Externalization
- java.nio buffers, channels
- Paths, Files, FileVisitor
- WatchService (directory monitoring)
- Asynchronous I/O
- Charset and encoding

---

## Classic I/O
```java
try (InputStream in = new FileInputStream("in.bin");
     OutputStream out = new FileOutputStream("out.bin")) {
    byte[] buf = new byte[8192];
    int n;
    while ((n = in.read(buf)) != -1) out.write(buf, 0, n);
}
```

## Readers/Writers
```java
try (BufferedReader br = Files.newBufferedReader(Path.of("data.txt"))) {
    br.lines().forEach(System.out::println);
}
```

## Serialization
```java
class Person implements Serializable { String name; transient int age; }
try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("p.bin"))) {
    oos.writeObject(new Person());
}
```

## NIO Buffers and Channels
```java
try (FileChannel ch = FileChannel.open(Path.of("file.txt"))) {
    ByteBuffer buf = ByteBuffer.allocate(1024);
    ch.read(buf);
    buf.flip();
}
```

## Paths and Files
```java
Path p = Path.of("logs/app.log");
Files.createDirectories(p.getParent());
Files.writeString(p, "hello\n", StandardOpenOption.CREATE, StandardOpenOption.APPEND);
```

## FileVisitor
```java
Files.walk(Path.of("."))
     .filter(Files::isRegularFile)
     .forEach(System.out::println);
```

## WatchService
```java
WatchService ws = FileSystems.getDefault().newWatchService();
Path dir = Path.of("inbox");
dir.register(ws, StandardWatchEventKinds.ENTRY_CREATE);
WatchKey key = ws.take();
```
