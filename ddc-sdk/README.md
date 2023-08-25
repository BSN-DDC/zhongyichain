###  Prerequisites

-   **Java 1.8 or later**

* **Create the project of China Mobile Chain in [BSN_DDC](https://ddc.bsnbase.com/main/index). Gateway URL: https://opbningxia.bsngate.com:18602/api/[project_id]/rpc**
* **Create the chain account in [BSN_DDC](https://ddc.bsnbase.com/main/index)**

### Maven

Add this dependency to your project's POM.xml file:

```xml
<dependency>
    <groupId>org.bouncycastle</groupId>
    <artifactId>bcprov-jdk15on</artifactId>
    <version>1.69</version>
</dependency>
<dependency>
    <groupId>org.bouncycastle</groupId>
    <artifactId>bcpkix-jdk15on</artifactId>
    <version>1.69</version>
</dependency>
<dependency>
    <groupId>one.block</groupId>
    <artifactId>eosiojava</artifactId>
    <version>1.0.0</version>
</dependency>
<dependency>
    <groupId>one.block</groupId>
    <artifactId>eosio-java-rpc-provider</artifactId>
    <version>1.0.0</version>
</dependency>

<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>RELEASE</version>
    <scope>compile</scope>
</dependency>
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>fastjson</artifactId>
    <version>1.2.41</version>
</dependency>
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.13.0</version>
</dependency>

<dependency>
    <groupId>com.squareup.okhttp3</groupId>
    <artifactId>okhttp</artifactId>
    <version>3.12.0</version>
</dependency>
<dependency>
    <groupId>com.squareup.okhttp3</groupId>
    <artifactId>logging-interceptor</artifactId>
    <version>3.12.0</version>
</dependency>
<dependency>
    <groupId>com.squareup.retrofit2</groupId>
    <artifactId>converter-scalars</artifactId>
    <version>2.5.0</version>
</dependency>
<dependency>
    <groupId>com.squareup.retrofit2</groupId>
    <artifactId>retrofit</artifactId>
    <version>2.5.0</version>
</dependency>

<dependency>
    <groupId>com.squareup.retrofit2</groupId>
    <artifactId>converter-jackson</artifactId>
    <version>2.5.0</version>
</dependency>
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>3.8.1</version>
</dependency>

<dependency>
    <groupId>io.jafka</groupId>
    <artifactId>jeos</artifactId>
    <version>0.9.15</version>
</dependency>
```

## Documentation

Gateway Access Instructions: [BSN Gateway](https://bsnbase.com/static/tmpFile/bzsc/openper/7-3-6.html)


### Configuration

#### Request EOS ddc contract account 
```java
ChainConfig.setDdcContractAndAccount("reddateddc22");
ChainConfig.setPk("private");
```


### Configure gateway

##### gateway URL

Gateway url must be set

```java
ChainConfig.setGatewayUrl("https://opbningxia.bsngate.com:18602/api/[project_id]/rpc/");
```

##### x-api-key

If you have enabled the project key in the BSN portal, it needs to be configured in the SDK. This configuration takes effect globally.

```java
ChainConfig.setGatewayApiKey("d8438f145351511503f572d632");
```


## Usage

```java
// Configuration
package com.example.basedata;

public class MyInfo {
    public static  String baseURL = "https://opbningxia.bsngate.com:18602/api/[project_id]/rpc/";
    public static  String ddcContractAndAccount = "baseURL"; //reddateddc22
    public static  String ddc_pk = "5KhNKCebmgu4xXyc6gyL4ccQyVS7HZq4kpMv6eS41H2NgCdw1DY";
   // Platform Owner
    public static String oper1_plateAccount2 = "plateacco112";
    public static String oper1_plateAccount2_pk = "5JpRaxKm3D1wFgLvux8RZ3d8asnsh3uyDVCaoKkG15Hnm6M3Hew";
    public static String oper1_plateAccount2_did = "bsn:oper1:pl2:3wxYHXwAm57grc9JUr2zrPHt9HC:ddc";
    // End user of the platform
    public static String oper1_plate2_account1 = "commonacc111";
    public static String oper1_plate2_account2 = "commonacc112";
    public static String oper1_plate2_account3 = "commonacc113";

}


package com.example.opr.ddc;

import com.alibaba.fastjson.JSON;
import com.bsn.eos.chain.ChainConfig;
import com.bsn.eos.chain.ChainUtil;
import com.bsn.eos.chain.vo.TableRows;
import com.bsn.eos.chain.vo.TableRowsReq;
import com.bsn.eos.service.impl.DDC721ServiceImpl;
import com.example.basedata.MyInfo;
import lombok.extern.slf4j.Slf4j;
import org.junit.Before;
import org.junit.Test;

import java.math.BigInteger;

@Slf4j
public class DDC721ServiceTest {
    DDC721ServiceImpl ddc721 = new DDC721ServiceImpl();

    @Before
    public void setDDCAccount(){
        ChainConfig.setGatewayUrl(MyInfo.baseURL);
        ChainConfig.setDdcContractAndAccount(MyInfo.ddcContractAndAccount);
//        ChainConfig.setPk("Replace with the private key of your EOS chain account");
    }
    
    // Generate DDCs
    @Test
    public void mint(){
        ChainConfig.setPk(MyInfo.oper1_plateAccount2_pk);
        ddc721.safeMint(MyInfo.oper1_plateAccount2, MyInfo.oper1_plateAccount2, "");
    }
    
    // Authorization
     @Test
     public void approve() {
        ChainConfig.setGatewayApiKey(MyInfo.oper1_plate2_account1_pk);
        BigInteger b = new  BigInteger("22");
        ddc721.approve(MyInfo.oper1_plateAccount2, MyInfo.oper1_plate2_account1, b);
    }
    
    // Authorization Inquiry
    @Test
    public void getApproved(){
        BigInteger b = new  BigInteger("0");
        log.info("Authorization Inquiry:"+ ddc721.getApproved(MyInfo.oper1_plateAccount2, MyInfo.oper1_plate2_account1, b));

    }
    
    // Account Authorization Inquiry
    @Test
    public void isApprovedForAll(){
        ChainConfig.setPk(MyInfo.oper2_plate1_account1_pk);
        log.info("Result of account authorization:" + ddc721.isApprovedForAll(MyInfo.oper1_plate2_account1, MyInfo.oper1_plate2_account3));
    }

    // Check balance
    @Test
    public void balanceOf(){
        log.info("Balance:"+ ddc721.balanceOf("123451234511"));
    }

    // Query the DDC owner
    @Test
    public void ownerOf(){
        TableRowsReq table = new TableRowsReq(ChainConfig.ddcContractAndAccount, ChainConfig.t1155accountTable, ChainConfig.ddcContractAndAccount);
        table.setIndex_position("3");
        table.setKey_type("i64");
        table.setLower_bound("3");
        table.setUpper_bound("3");
        TableRows rows = ChainUtil.getInstance().getTableRows(table);
        System.out.println("Get the owner with ddcid 3:"+ JSON.toJSONString(rows, true));
    }

    // Get DDCURI
    @Test
    public void ddcURI(){
        BigInteger b = new  BigInteger("0");
        log.info("Get DDCURI:" + ddc721.ddcURI(b));
    }

    @Test
    public void get_table_rows() {
        // Query all 721 DDCs with owner yqyyyyyyyyyy
        TableRowsReq table = new TableRowsReq(ChainConfig.ddcContractAndAccount, ChainConfig.s21accountTable, ChainConfig.ddcContractAndAccount);
        table.setIndex_position("2");
        table.setKey_type("name");
        table.setLower_bound("yqyyyyyyyyyy");
        table.setUpper_bound("yqyyyyyyyyyy");
        table.setReverse(true);
        table.setLimit(1);
        TableRows rows = ChainUtil.getInstance().getTableRows(table);
        System.out.println("Get all 721 DDCs hold by the owner yqyyyyyyyyyy in rows: " + JSON.toJSONString(rows, true));
    }
}

@Slf4j
public class DDC721ServiceTest {
    DDCCrossChainServiceImpl crosschain = new DDCCrossChainServiceImpl();
    
    // 发起跨链
    @Test
    public void crossChainTransfer() {
        crosschain.crossTrans(
                sender, // 发起跨链的签名者账户
                1, // 1表示721
                signer, // 目标链签名者账户
                to, // 目标链接收者账户
                ddcId,
                data, // 附加数据
                toChainId, // 目标链Id
                toCCAddr, // 目标链跨链合约地址
                vo.getFuncName() // 目标链合约方法名
        );
    }
}
```

