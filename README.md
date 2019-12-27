## **What is CPViewer?**

CPViewer is an open-source community tool which simplifies the way to get a very detailed visual insights into:

1) Exported cpview histories with charts related to CPU, memory, connections and packet rates, throughputs, RX&TX drops etc. using the visualization metrics tool called Grafana;

2) OS analysis (.info file) - healthcheck report for "known issues" and "things not to miss";

The tool comes within an .ova (exported VM) with everything already preconfigured.
 

The main benefits are:
analyzing and identifying performance bottlenecks in minutes
user-friendly: just upload it to web-site (no docker or other components needed) 
Integrated OS analysis tool for richer results (healthcheck script)
available to both customers and partners
 
CPViewer .ova file download - [HERE](https://drive.google.com/file/d/1_OAGH3AsrOtE1B8MdagtP_aIWS_XbyOP/view).
 
CPViewer guide - [HERE](https://drive.google.com/file/d/1SucAFhLKy0HzE2jJWisvTR8Ks4Kc3ksV/view).
 

## **How to use it?**
 

Video [LINK](https://www.youtube.com/watch?v=giZ49CqtLm0&hd=1) explains all you need to do to get CPViewer up and running - 5 simple steps.

## **Written step by step guide:**
 

**1. Import the VM:**

a. Download and import OVA image into your VMWare environment – DOWNLOAD LINK.

b. VM’s network adapter is set to NAT, it has IPv4 – 10.8.0.15, default gw – 10.8.0.2 and DNS – 8.8.8.8 predefined already, but you can adjust this by your needs;

c. Adjust your VMWare NAT adapter;

d. Credentials:
- OS: root/vpn123
- Grafana: admin/Vpn123!

***NOTE: Your VM must have internet access.**

 

**2. Working with CPViewer portal:**

a. CPViewer portal can process two types of data:

1) CPInfo files (contains cpinfo and cpview files) -> you will get 2 reports, grafana cpview insights and cpinfo OS analysis report (in separate tab);

2) CPView (.dat or .gz – with .dat in it) files only;

***NOTE: In case you are using type 1, please be aware that you need to either configure your browser to allow pop-ups for http://10.8.0.15:80 in order to get the CPInfo healthcheck report. Other option is just to go to http://10.8.0.15/healthcheck_reports manually and select a report you need.**

b. After setting up the VM, open any browser and go to CPViewer portal -> http://10.8.0.15.

Select upload method:

1) Manual/attachment upload: you can submit .dat or .gz file (which contains .dat);

2) Google link (server will automatically download file from GDrive). In this case solid upload link is highly recommended;

***NOTE: You can pick one of the two methods, not both at the same time;**

c. Enter customer`s name (this will be used for name db and datasource of cpview; d. Select version from which cpview was exported – R77.30 – R80.10 or R80.20+;

e. If you did all of the above, select the submit button and wait for your reports to get created;

***NOTE: Speed of the processing will depetend on the size of the file (upload time + querying/healthcheck.sh execution through the .dat/.info and taking all the relevant info).**



**3. After you get redirected to Grafana you will be able to see your cpview visualized through graphs focused on different parameters. In case you uploaded CPInfo file you will also get GW`s healthcheck report in a separate tab.**
**Few useful GrafanaUI details:**

- Top left corner – selected datasource (datasources will automatically be deleted on weekly basis);

- On menu at the far left you will be able to see possible dashboards (do not need to be changed since everything related to your cpview is automatically provisioned);

- Top right corner – time span which we are looking into (this is also automatically set from the first to the last timestmmp from your cpview);

- When clicking on different views you will be able to adjust some parameters or queries according to your needs;

***NOTE: All datasources – their dbs and healthcheck reports are being automatically deleted every Monday at midnight. If you do not want this – enter crontab using command crontab – e from CLI, erase the camm of deleteALL.php and/or delete_hc.sh script/s and save it.**

 

***DISCLAIMER - This open source tool is provided “As Is”.  No representations or warranties are provided with the use of this tool.**
