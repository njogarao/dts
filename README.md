# Dpdk test suite

http://dpdk.org/doc/dts/gsg/intro.html

Please install below third party python modules on your tester machine.

   python-xlwt
   python-pexpect
   numpy
   python-docutils
   pcapy
   python-xlrd

Build kernel for OcteonTX
--------------------------
- Download OCTEONTX-SDK-6.2.0 rpm + Patch1 from diablo (Diablo path: sw_qa/releases/octeontx/sdk)

- Extract RPM and follow the README file for how to build kernel.

Please make sure below drivers as a module in kernel.

 CONFIG_VFIO=m
 CONFIG_VFIO_IOMMU_TYPE1=m
 CONFIG_THUNDER_NIC_VF=m
 
 
Below are the steps to run dts from x86.
----------------------------------------

- Download dts from below mentioned path.

https://github.com/njogarao/dts.git

- Please change 'ip address, username, passwd' in execution.cfg and conf/crbs.py files respectively.

- Download dpdk sources from dpdk.org/master , release or tag and Create a tar file 
    Ex:
      $ cd <Download path>
      $ git clone  git://dpdk.org/dpdk
      $ tar -czf dpdk.tar.gz  dpdk/
  
- Copy 'dpdk.tar.gz' file to  'dts/dep' folder.
  
- Build dpdk on DUT with cavium toolchain, please copy toolchain to DUT and add 'toolchainpath=/home/source.sh'  in dts/execution.cfg file.
      Ex: 
      
      On my setup, copied toolchain to /root/ folder.

      root@localhost:/home# cat source.sh

      export LD_LIBRARY_PATH=/root/thunderx-gcc_5_3-421/thunderx-gcc_5_3-421/lib64:$LD_LIBRARY_PATH

      export PATH=/root/thunderx-gcc_5_3-421/thunderx-gcc_5_3-421/bin:${PATH}


- Please find log files and testcase summary files under output folder.

      'test_results.xls' has all the testcases status with testcase name.
   
       $testcasename.log has complete test run details.
  
- If we run any performance tests, performance results files under 'rst_report/arm64-thunderx-linuxapp-gcc/cavium/'
       $testcasename.rst file has perfromance numbers. we can convert this rst file into html using 'rst2html.py' ( Install 'sphinx' package to get this utilities)
 
       $testcasename_ Annex.rst  has all the test commands to capture the performance.
  
