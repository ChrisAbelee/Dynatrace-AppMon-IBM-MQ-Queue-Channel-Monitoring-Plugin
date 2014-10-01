<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title>IBM MQ Queue Channel Monitoring Plugin</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
    <meta http-equiv="X-UA-Compatible" content="IE=EmulateIE8" />
    <meta content="Scroll Wiki Publisher" name="generator"/>
    <link type="text/css" rel="stylesheet" href="css/blueprint/liquid.css" media="screen, projection"/>
    <link type="text/css" rel="stylesheet" href="css/blueprint/print.css" media="print"/>
    <link type="text/css" rel="stylesheet" href="css/content-style.css" media="screen, projection, print"/>
    <link type="text/css" rel="stylesheet" href="css/screen.css" media="screen, projection"/>
    <link type="text/css" rel="stylesheet" href="css/print.css" media="print"/>
</head>
<body>
                <h1>IBM MQ Queue Channel Monitoring Plugin</h1>
    <div class="section-2"  id="112462681_IBMMQQueueChannelMonitoringPlugin-Overview"  >
        <h2>Overview</h2>
    <p>
    </p>
    <p>
    </p>
    <p>
            <img src="images_community/download/attachments/112462681/icon.png" alt="images_community/download/attachments/112462681/icon.png" class="confluence-embedded-image image-center" />
        This monitor collects statistical information from the MQ Queue Manager.    </p>
    </div>
    <div class="section-2"  id="112462681_IBMMQQueueChannelMonitoringPlugin-PluginDetails"  >
        <h2>Plugin Details</h2>
    <div class="tablewrap">
        <table>
<thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" ">    <tr>
            <td rowspan="1" colspan="1">
        <p>
Plug-In Versions    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="attachments_178487520_1_com.dynatrace.plugin.MQQueueChannelMonitorUpdated_0.9.1.6.jar">com.dynatrace.plugin.MQQueueChannelMonitorUpdated_0.9.1.6.jar</a>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
dynaTrace Versions    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
4.2 and higher    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
Author    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
Asad Ali (<a href="mailto:asad.ali@compuware.com">asad.ali@compuware.com</a>)    </p>
    <p>
Eugene Turetsky (<a href="mailto:eugene.turetsky@compuware.com">eugene.turetsky@compuware.com</a>) added z/OS support    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
License    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="attachments_5275722_2_dynaTraceBSD.txt">dynaTrace BSD</a>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
Support    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="https://community/display/DL/Support+Levels#SupportLevels-Community">Not Supported </a>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
Known Problems    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
Release History    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
2013-03-05 Initial Release<br/>2013-09-04 Added z/OS support (<a href="mailto:eugene.turetsky@compuware.com">eugene.turetsky@compuware.com</a>)<br/>2014-01-30 Fixed issue with duplicate channels (<a href="mailto:eugene.turetsky@compuware.com">eugene.turetsky@compuware.com</a>)<br/>2014-03-07 Re-written MQ Queue channel management piece of the plugin (<a href="mailto:eugene.turetsky@compuware.com">eugene.turetsky@compuware.com</a>)<br/>Changes include:    </p>
<ol class=" "><li class=" ">    <p>
Aggregation on channel level. Aggregation is done by number-of-messages, bytes-sent, bytes-received, buffers-sent, buffers-received.    </p>
</li><li class=" ">    <p>
Added missing connections for given channels. For these connections channel names are composed with &ldquo;channel-name&rdquo; and &ldquo;connection-name&rdquo; separated by &ldquo;|&rdquo; (pipe) character. This rule does not apply to the channels which have aggregated statistics.    </p>
</li><li class=" ">    <p>
Aggregated channels do not have &ldquo;status&rdquo; and &ldquo;substate&rdquo; measures.    </p>
</li><li class=" ">    <p>
Added the following fields for channel&rsquo;s aggregate records and connection channels:    </p>
<ol class=" "><li class=" ">    <p>
CHANNEL_TYPE    </p>
</li><li class=" ">    <p>
LAST_MSG_DATE    </p>
</li><li class=" ">    <p>
LAST_MSG_TIME    </p>
</li><li class=" ">    <p>
CURRENT_SHARING_CONVS for SVRCONN channels    </p>
</li></ol></li><li class=" ">    <p>
Added two new plugin parameters for the LAST_MSG_DATE and LAST_MSG_TIME fields returned by the MQCMD_INQUIRE_CHANNEL_STATUS command:    </p>
<ol class=" "><li class=" ">    <p>
Date Format, default value is &quot;yyyy-MM-dd&quot;    </p>
</li><li class=" ">    <p>
Time Format, default value is &quot;HH.mm.ss&quot;    </p>
</li></ol></li><li class=" ">    <p>
On the aggregate level    </p>
<ol class=" "><li class=" ">    <p>
Channel type is a type of the last connection channel for given channel.    </p>
</li><li class=" ">    <p>
LAST_MSG_DATE and LAST_MSG_TIME are the latest date and time of the channel connections for given channel    </p>
</li><li class=" ">    <p>
CURRENT_SHARING_CONVS is sum of CURRENT_SHARING_CONVS of the underlying channel connections for given channel    </p>
</li></ol></li></ol>    <p>
2014-04-11 Added extended filtering capabilities for channel names: channel name filter parameter now can contain list of semicolon (&quot;;&quot;)  separated filters. (<a href="mailto:Eugene.turetsky@compuware.com">eugene.turetsky@compuware.com</a>)<br/>2014-07-13 Fixed issue related to SSL communication (<a href="mailto:eugene.turetsky@compuware.com">eugene.turetsky@compuware.com</a>)    </p>
    <p>
2014-09-13 Fixes include (<a href="mailto:eugene.turetsky@compuware.com">eugene.turetsky@compuware.com</a>):    </p>
<ul class=" "><li class=" ">    <p>
    <span style="color: #333333;">
Added two new parameters to avoid using the default SYSTEM.DEFAULT.MODEL.QUEUE queue. See the IBM tech note <a href="http://www-01.ibm.com/support/docview.wss?uid=swg21675366">here</a> for details. These parameters are:    </span>
    </p>
<ul class=" "><li class=" ">    <p>
    <span style="color: #333333;">
Model Queue Name;    </span>
    </p>
</li><li class=" ">    <p>
    <span style="color: #333333;">
Reply Queue.    </span>
    </p>
</li></ul></li></ul>    <p>
    <span style="color: #333333;">
 <strong class=" ">Notes</strong>     </span>
    </p>
<ol class=" "><li class=" "><ol class=" "><li class=" "><ol class=" "><li class=" ">    <p>
    <span style="color: #333333;">
Use of custom Model Queues is available for <i class=" ">distributed</i> platform only. We will update this page as soon as this feature will be available for z/OS platform.    </span>
    </p>
</li><li class=" ">    <p>
    <span style="color: #333333;">
APAR IT04221 should be applied for Websphere MQ versions 7.0.1 thru 8.0 in order to use asterisk (*) in the Reply Queue name. This APAR is included in the 7.5.0.5 fix pack.      </span>
    </p>
</li></ol></li></ol></li></ol><ul class=" "><li class=" ">    <p>
    <span style="color: #333333;">
     </span>
Fixed issue associated with the en-queue/de-queue measures.    </p>
</li></ul>            </td>
        </tr>
</tbody>        </table>
            </div>
    </div>
    <div class="section-2"  id="112462681_IBMMQQueueChannelMonitoringPlugin-ProvidedMeasures"  >
        <h2>Provided Measures</h2>
    <div class="section-3"  id="112462681_IBMMQQueueChannelMonitoringPlugin-QueueManager"  >
        <h3>Queue Manager</h3>
<ul class=" "><li class=" ">    <p>
Status    </p>
</li></ul>    </div>
    <div class="section-3"  id="112462681_IBMMQQueueChannelMonitoringPlugin-Queue"  >
        <h3>Queue</h3>
<ul class=" "><li class=" ">    <p>
CURRENT_Q_DEPTH    </p>
</li><li class=" ">    <p>
DEF_PRIORITY    </p>
</li><li class=" ">    <p>
DEQUEUE_COUNT    </p>
</li><li class=" ">    <p>
ENQUEUE_COUNT    </p>
</li><li class=" ">    <p>
INHIBIT_GET    </p>
</li><li class=" ">    <p>
INHIBIT_PUT    </p>
</li><li class=" ">    <p>
MAX_MSG_LENGTH    </p>
</li><li class=" ">    <p>
MAX_Q_DEPTH    </p>
</li><li class=" ">    <p>
OPEN_INPUT_COUNT    </p>
</li><li class=" ">    <p>
OPEN_OUTPUT_COUNT    </p>
</li><li class=" ">    <p>
OLDEST_MSG_AGE    </p>
</li><li class=" ">    <p>
UNCOMMITTED_MSGS    </p>
</li><li class=" ">    <p>
HIGH_Q_DEPTH    </p>
</li><li class=" ">    <p>
INT_LAST_GET    </p>
</li><li class=" ">    <p>
INT_LAST_PUT    </p>
</li><li class=" ">    <p>
Q_TIME_SHORT    </p>
</li><li class=" ">    <p>
Q_TIME_LONG    </p>
</li></ul>    </div>
    <div class="section-3"  id="112462681_IBMMQQueueChannelMonitoringPlugin-Channel"  >
        <h3>Channel</h3>
<ul class=" "><li class=" ">    <p>
STATUS    </p>
</li><li class=" ">    <p>
SUBSTATE    </p>
</li><li class=" ">    <p>
MSGS    </p>
</li><li class=" ">    <p>
BYTES_SENT    </p>
</li><li class=" ">    <p>
BYTES_RECEIVED    </p>
</li><li class=" ">    <p>
BUFFERS_SENT    </p>
</li><li class=" ">    <p>
BUFFERS_RECEIVED    </p>
</li></ul>    </div>
    </div>
    <div class="section-2"  id="112462681_IBMMQQueueChannelMonitoringPlugin-Configuration"  >
        <h2>Configuration</h2>
    <p>
This monitor uses IBM PCF library to connect to the MQ Manager and collect the statistics. The plugin can be run on any collector. In order for this plugin to work, ensure that SYSTEM.ADMIN.SVRCONN type channel is created on the MQ Manager. This is the channel that the MQ Manager would publish the statistics information.    </p>
    <p>
NOTE: This plugin requires dynaTrace server version 4.2.0.3170 or higher. This monitor works for IBM MQ 7.0 and higher    </p>
    </div>
    <div class="section-2"  id="112462681_IBMMQQueueChannelMonitoringPlugin-Installation"  >
        <h2>Installation</h2>
    <p>
Import the Plugin into the dynaTrace Server. For details how to do this please refer to the <a href="https://apmcommunity.compuware.com/community/display/DOCDT50/Plugins">dynaTrace documentation</a>.    </p>
    </div>
            </div>
        </div>
        <div class="footer">
        </div>
    </div>
</body>
</html>
