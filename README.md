# MTConnect FANUC CNC Adapter

## Run the script

### Installing FOCAS2 library

FOCAS2 library is required to interface with the FANUC CNC machine controller. 

Once you have the FOCAS2 library, go into the directory containing the library and follow the steps below, 

1. Install the FOCAS2 library

```shell
sudo cp libfwlib32.so.1.0.0 /usr/local/lib/libfwlib32.so.1.0.0 
```

```shell
sudo ldconfig
```

```shell
sudo ln -s /usr/local/lib/libfwlib32.so.1.0.0 /usr/local/lib/libfwlib32.so
```

2. Copy the FOCAS2 header file to the right location

```shell
sudo cp Fwlib32.h ~/MTConnect_FANUC-adapter/lib/FOCAS2
```

This should complete the steps required to install the FOCAS2 library.

### Compiling and running the adapter

Once the FOCAS2 library is installed, navigate to the directory of this repository.

1. Run cmake and then make

```shell
cmake .
```

```shell
make
```

2. Edit the `adapter.ini` file to configure FOCAS2 connection and other parameters

3. Run the adapter

```shell
./FanucAdapter
```

The adapter should start running by this point and connect to the CNC machine.

## Directory Structure

## TODO

- [ ] Ability to compile for different FANUC CNC controller series
- [ ] Adding more data items to be sent out by the adapter

## Acknowledgements

- MTConnect Adapter Repository    -> https://github.com/mtconnect/adapter
- Reading ".ini" files            -> https://github.com/compuphase/minIni
