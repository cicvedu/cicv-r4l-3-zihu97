# Create a Character Device

## Step 1: Implement Read and Write Functions

```rust
impl file::Operations for RustFile {
    type Data = Box<Self>;

    fn open(_shared: &(), _file: &file::File) -> Result<Box<Self>> {
        Ok(
            Box::try_new(RustFile {
                inner: &GLOBALMEM_BUF
            })?
        )
    }

    fn write(this: &Self, _file: &file::File, reader: &mut impl IoBufferReader, offset: u64) -> Result<usize> {
        let offset = offset.try_into()?;
        let mut vec = this.inner.lock();
        let len = core::cmp::min(reader.len(), vec.len().saturating_sub(offset));
        reader.read_slice(&mut vec[offset..][..len])?;
        Ok(len)
    }

    fn read(this: &Self, _file: &file::File, writer: &mut impl IoBufferWriter, offset: u64) -> Result<usize> {
        let offset = offset.try_into()?;
        let vec = this.inner.lock();
        let len = core::cmp::min(writer.len(), vec.len().saturating_sub(offset));
        writer.write_slice(&vec[offset..][..len])?;
        Ok(len)
    }
}
```

Rebuild the kernel.

## Step 2: Create a Device File

In the QEMU Linux environment:

```bash
insmod rust_chrdev.ko
echo 1 > /dev/cicv
cat /dev/cicv
```
![alt text](images/9.png)

## Questions & Answers

## Questions

作业5中的字符设备/dev/cicv是怎么创建的？它的设备号是多少？它是如何与我们写的字符设备驱动关联上的？

## Answers

通过以下方式创建
```
echo "mknod /dev/cicv c 248 0" >> etc/init.d/rcS
```
主设备号是248，次设备号是0

```
~ # cat /proc/devices | grep 248
248 rust_chrdev
```
