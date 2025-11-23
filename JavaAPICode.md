Perfect — let’s turn that demo snippet into a **cleaner, production‑ready version** with better structure, exception handling, and configuration management.  

---

## ✨ Improvements Made
- **Externalized configuration**: No hardcoded values; use properties or environment variables.
- **Robust exception handling**: Catch and log errors clearly.
- **Resource cleanup**: Ensure sessions are closed in `finally`.
- **Logging**: More informative messages.
- **Reusable methods**: Easier to maintain.

---

## 🧑‍💻 Refactored Code Example

```java
import java.text.DateFormat;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Properties;

import javax.security.auth.Subject;

import org.apache.log4j.Logger;
import org.apache.log4j.xml.DOMConfigurator;

import com.filenet.api.core.Connection;
import com.filenet.api.core.Factory;
import com.filenet.api.util.UserContext;

import filenet.vw.api.*;

public class FileNetConnection {

    private static final Logger log = Logger.getLogger(FileNetConnection.class);

    private final String userName;
    private final String password;
    private final String uri;
    private final String connectionPoint;
    private final String jaasConfig;
    private final String rosterName;
    private final String startDateStr;
    private final String endDateStr;
    private final int deleteCount;
    private final boolean deleteFlag;

    public FileNetConnection(Properties props) {
        this.userName = props.getProperty("CONNECTION_USER");
        this.password = props.getProperty("CONNECTION_PASSWORD");
        this.uri = props.getProperty("CONNECTION_URL");
        this.connectionPoint = props.getProperty("CONNECTION_POINT");
        this.jaasConfig = props.getProperty("CONNECTION_JAAS_PATH");
        this.rosterName = props.getProperty("CONNECTION_ROSTER");
        this.startDateStr = props.getProperty("START_DATE");
        this.endDateStr = props.getProperty("END_DATE");
        this.deleteCount = Integer.parseInt(props.getProperty("DELETE_COUNT", "100"));
        this.deleteFlag = Boolean.parseBoolean(props.getProperty("DELETE_FLAG", "false"));
    }

    public int purgeWorkItems() {
        VWSession vwSession = null;
        try {
            System.setProperty("java.security.auth.login.config", jaasConfig);

            Connection conn = Factory.Connection.getConnection(uri);
            Subject subject = UserContext.createSubject(conn, userName, password, "FileNetP8WSI");
            UserContext.get().pushSubject(subject);

            vwSession = new VWSession();
            vwSession.setBootstrapCEURI(uri);
            vwSession.logon(userName, password, connectionPoint);

            log.info("Connected to PE. ObjectStore: " + vwSession.getObjectStoreSymbolicName());

            VWRoster roster = vwSession.getRoster(rosterName);
            log.info("Roster fetched: " + rosterName + " with count: " + roster.fetchCount());

            DateFormat formatter = new SimpleDateFormat("dd/MM/yyyy");
            long startDateMS = formatter.parse(startDateStr).getTime() / 1000;
            long endDateMS = formatter.parse(endDateStr).getTime() / 1000;

            String queryFilter = "F_StartTime > " + startDateMS + " AND F_StartTime < " + endDateMS;
            VWRosterQuery query = roster.createQuery(null, null, null,
                    VWRoster.QUERY_READ_UNWRITABLE, queryFilter, null,
                    VWFetchType.FETCH_TYPE_WORKOBJECT);

            log.info("Query returned count: " + query.fetchCount());

            int count = 0;
            while (count < deleteCount && query.hasNext()) {
                VWWorkObject workObject = (VWWorkObject) query.next();
                if (deleteFlag) {
                    String wobNumber = workObject.getWorkflowNumber();
                    workObject.doDelete(true, true);
                    log.info("Deleted work item: " + wobNumber);
                    count++;
                }
            }
            log.info("Total deleted work items: " + count);
            return count;

        } catch (Exception e) {
            log.error("Error during purge operation", e);
            return -1;
        } finally {
            if (vwSession != null) {
                try {
                    vwSession.logoff();
                    log.info("Logged off from PE.");
                } catch (VWException e) {
                    log.warn("Error during logoff", e);
                }
            }
        }
    }
}
```

---

## 🛠 How to Use
1. Create a `config.properties` file:
   ```properties
   CONNECTION_USER=P8Admin
   CONNECTION_PASSWORD=filenet
   CONNECTION_URL=http://100.10.10.213:9080/wsi/FNCEWS40MTOM/
   CONNECTION_POINT=fncp
   CONNECTION_JAAS_PATH=../PEPurge/jaas.conf.WSI/
   CONNECTION_ROSTER=P8Hub
   START_DATE=01/09/2016
   END_DATE=11/09/2016
   DELETE_COUNT=100
   DELETE_FLAG=true
   ```
2. Load properties in your main class:
   ```java
   Properties props = new Properties();
   props.load(new FileInputStream("config.properties"));
   FileNetConnection fnConn = new FileNetConnection(props);
   fnConn.purgeWorkItems();
   ```

---
