insert 날짜 형 변환

```
insert table ('xx','xx','xx'
)VALUES(
         #trptId#
         , #trptNo#
         , #prlcNo#
         , TO_CHAR(TO_DATE(#prlcEndDt#,'YYYY-MM-DD'),'YYYYMMDD')
         )

```

update 날짜 형 변환

```
<update id="TrptPrlcDAO.updateTrptPrlc">
      UPDATE TB_IP_IT_TRPT_PRLC
      SET TRPT_ID = #trptId#
      , TRPT_NO = #trptNo#
      <isNotEmpty property="prlcNo">
      , PRLC_NO = #prlcNo#
      </isNotEmpty>
      <isNotEmpty property="prlcEndDt">
      , PRLC_END_DT = TO_CHAR(TO_DATE(#prlcEndDt#,'YYYY-MM-DD'),'YYYYMMDD')
      </isNotEmpty>
      
```

select 날짜 형 변환

```
SELECT TRPT_ID
         , TRPT_NO
         , PRLC_NO
         , TO_CHAR(TO_DATE(PRLC_END_DT,'YYYYMMDD'),'yyyy-MM-dd') AS PRLC_END_DT
         , BSNS_CD
         , FN_GET_CODE_NM('BSNS_CD', BSNS_CD, 'CODE_DETL_NM') AS BSNS_NM
         , PRC_PLY_SCL
         , PRC_PLY_PYCS
         , PRC_PLY_FLTR
         , LCN_STAT_CD
         , LCN_STAT_MSG
         , LCN_STAT_UPD_ID
         , LCN_STAT_UPD_DATE
         , TO_CHAR(FCLT_AFRM_DATE, 'YYYY-MM-DD') AS FCLT_AFRM_DATE
         , FCLT_AFRM_STAT_CD
         , FCLT_AFRM_STAT_UPD_ID
         , FCLT_AFRM_STAT_UPD_DATE
         , LCN_CNCL_ID
         , LCN_CNCL_DATE
         , RMK
         , REG_USER_ID
         , FN_GET_USER_NM(REG_USER_ID) AS REG_USER_NM
         , TO_CHAR(REG_DATE, 'YYYY-MM-DD HH24:MI:SS') AS REG_DATE
         , UPD_USER_ID
         , FN_GET_USER_NM(UPD_USER_ID) AS UPD_USER_NM
         , TO_CHAR(UPD_DATE, 'YYYY-MM-DD HH24:MI:SS') AS UPD_DATE 
      FROM TB_IP_IT_TRPT_PRLC
      WHERE 1 = 1
      AND TRPT_NO = #trptNo#

```












