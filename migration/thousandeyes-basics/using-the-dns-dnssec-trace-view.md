# Using the DNS DNSSEC Trace view

When you create any DNSSEC Trace test, you get access to the DNS DNSSEC Trace view.  The DNSSEC Trace view leverages the ThousandEyes standard layout, documented here: [https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC).  

This article highlights specifics shown in the DNSSEC Trace view.

## Example

This example shows the result of a globally distributed DNSSEC Trace test, targeting fbi.gov A 

IMAGE MISSING

## View Specifics

The DNSSEC Trace test measures worldwide validity by validating the keychain for the target DNS record from the bottom up.  This view is very simple and purposeful: a DNSSEC query has a binary response - either it works, or it doesn't. - this makes the view very simple.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without an Agent selected</b>
        </p>
        <p>For DNSSEC View, results are shown under two tabs:</p>
        <p><b>Map: </b>Shows worldwide validity percentage measurements of the target
          domain and record type calculated from all Agents assigned to the test.</p>
        <p>IMAGE MISSING</p>
        <p><b>Table: </b>To view Agent specific results, click on the Details link
          under Status column.</p>
        <p>IMAGE MISSING
          <br />The timeline plots the graph of the average validity of the target domain
          and record type calculated from all Agents assigned to the test.
          <br />IMAGE MISSING
          <br />
        </p>
      </th>
      <th style="text-align:left">
        <p><b>With an Agent selected</b>
        </p>
        <p>For DNSSEC View, results are shown under two tabs:</p>
        <p><b>Map: </b>Shows whether the results from that Agent for the target domain
          and record type are OK (valid) or Invalid. Click on View Details for DNSSEC
          trace data.
          <br />IMAGE MISSING</p>
        <p><b>Table: </b>To view Agent specific results, click on the Details link
          under Status column.</p>
        <p>IMAGE MISSING</p>
        <p>The timeline plots the validity percentage (0 or 100) results from the
          Agent as a line graph over the average validity measurements, calculated
          from all Agents, for the selected date and time.</p>
        <p>IMAGE MISSING</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>Clicking the View Details link opens a modal dialog with two tabs related to the trace data, showing trust tree detailed information, and data chain detailed information for the query.  Examples of this detailed information can be found below:

### Trust tree detailed information for fbi.gov:A

```text
fbi.gov. (A)
|---fbi.gov. (DNSKEY keytag: 32497 alg: 7 flags: 256)
    |---fbi.gov. (DNSKEY keytag: 24840 alg: 7 flags: 257)
    |---fbi.gov. (DS keytag: 24840 digest type: 1)
    |   |---gov. (DNSKEY keytag: 343 alg: 7 flags: 256)
    |       |---gov. (DNSKEY keytag: 53138 alg: 7 flags: 257)
    |       |---gov. (DS keytag: 53138 digest type: 1)
    |       |   |---. (DNSKEY keytag: 40323 alg: 8 flags: 256)
    |       |       |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
    |       |---gov. (DS keytag: 53138 digest type: 2)
    |           |---. (DNSKEY keytag: 40323 alg: 8 flags: 256)
    |               |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
    |---fbi.gov. (DS keytag: 24840 digest type: 2)
        |---gov. (DNSKEY keytag: 343 alg: 7 flags: 256)
            |---gov. (DNSKEY keytag: 53138 alg: 7 flags: 257)
            |---gov. (DS keytag: 53138 digest type: 1)
            |   |---. (DNSKEY keytag: 40323 alg: 8 flags: 256)
            |       |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
            |---gov. (DS keytag: 53138 digest type: 2)
                |---. (DNSKEY keytag: 40323 alg: 8 flags: 256)
                    |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
```

### Data chain detailed information for fbi.gov:A

```text
;; rcode: NOERROR
;; qtype: DNSKEY
rrset:
.	172800	IN	DNSKEY	256 3 8 AwEAAaYCmqKPwuX/gckHK0xh0oPMzbLAR9BhlOOfvxG537GKKs0subofzyzNjsXZLefCeagHfjT6HKzkV6Pzs31LtgJRFDn9lsZeOXtFIP4t2SpQkxl1Sw8L0VhNFLb6BwKhD1yz7wKh96wpErLHilwDSL9ScwlfTvRwCAscwh5vQtcd ;{id = 40323 (zsk), size = 1024b}
.	172800	IN	DNSKEY	257 3 8 AwEAAagAIKlVZrpC6Ia7gEzahOR+9W29euxhJhVVLOyQbSEW0O8gcCjFFVQUTf6v58fLjwBd0YI0EzrAcQqBGCzh/RStIoO8g0NfnfL2MTJRkxoXbfDaUeVPQuYEhg37NZWAJQ9VnMVDxP/VHL496M/QZxkjf5/Efucp2gaDX6RS6CXpoY68LsvPVjR0ZSwzz1apAzvN9dlzEheX7ICJBBtuA6G3LQpzW5hOA2hzCTMjJPJ8LbqF6dsV6DoBQzgul0sGIcGOYl7OyQdXfZ57relSQageu+ipAdTTJ25AsRTAoub8ONGcLmqrAmRLKBP1dfwhYB4N7knNnulqQxA+Uk1ihz0= ;{id = 19036 (ksk), size = 2048b}
sigs:
.	172799	IN	RRSIG	DNSKEY 8 0 172800 20130316235959 20130302000000 19036 . Aax0kYQWK9WaKmeCUT5wwrMtpqWTEiW+YBk60HvdyZ+/Ajg2dth/MubrjWyKGsG+KR1qwDBQE9jupbpjyRn/x54SBxrDWYIcbChhrrm1sVicWfjIdMPCAV0ZcCTl5Lj+9Nchq5UGGS1Qrf8yHnMCHxHXQM2iL84NDVyWk0OYTR2tPdK1TMneQkAo4v26zRKikuJKMImxRYmCUrQdLNqldDE7s8Hxy1j5b+tj95qUgW0pf95RwEFygMBzYvb0ESafpPFBTFsdTFBB1V/vYWQTdy5i+nD3e7OU6msU3sH63M7O63Um5Xi0eSvxhQqrOjK/i6Q9b0MPTe+Sp3IPdly9jg==
---
;; rcode: NOERROR
;; qtype: DS
rrset:
gov.	86400	IN	DS	53138 7 1 35d81501cc594683875872282fe73054cfe619de
gov.	86400	IN	DS	53138 7 2 5aec256412bc1fec92b8fddb4493b585e9406541cf8c952bfe6e27acb3a20766
sigs:
gov.	86400	IN	RRSIG	DS 8 1 86400 20130312000000 20130304230000 40323 . BhxfK1XTuBzk21N19fF6Xd/EHriWnKSJi+C76gkADm/B4nkg06JKJE0r4Azxh11tU3f2cvurRQXPZpyoFH0/Pyrp36eke0uJYAC+06nACkbnPelexGmiRbQXW6inCQ+qmKkb9S0secB5PJhO9Xx2ukh0MEZmd4WOwLEHZyvgPMw=
---
;; rcode: NOERROR
;; qtype: DNSKEY
rrset:
gov.	86400	IN	DNSKEY	256 3 7 AQPldT85ootQcdAmTd6MgGU2r8dO0dXU+UlqUIkzzenFK55ZOr7eP3BqAcBCfljgK0zrIU4axiqniK8W3C6X9JlX3V/CB0dtjOEBfHRQEtT/JQGqVfVipLpBAqqiDSUH9gMIbC2Isl8aGm/tTNX0vxaFdipr+yTQAbrwHkmRazYJ4q6d7AgYOH2NxxFIauxo1PzU0f/yoZW3+oxOHITx19/9eBAzXjyZzy0UZIXN7nxMSu5WTR9tEl9GGA0pEf3cBOsaI2zEF3QldU6bPdgKn0RJHuVfowJJaEhxaOEzGApEfFPiLOYW3bkqGXx7C2cvMb2urdw6FqBSZuUh+k2DmWml ;{id = 32416 (zsk), size = 2048b}
gov.	86400	IN	DNSKEY	257 3 7 AQO7tpGcHVEdeAwk47cj6Tuc3dvAUktIQ1vMu8mGtGYQ8F6vSOgViE0tmzPtVFrV9E6kY1jLYCh+oKPWn7efpQVMkqc+2b9ECYk/81fA4Vb0BfyYKKhiW7T1uNX4rC03JZa2u8iOHwqq4BRVplksFXCGn47i2Sosa5KuqCNBqUA0oyPTEbxkyNo3Q6l8ZcscILqbvWZ0BJKaLCTtj08Nj35LTqd/XVoEObp48A21Pqyi6Kiblh9H6NoLtqhlvP5+8AujtINJ+sTUQZYgqt9iFQp2AH4HvyJdw8Vkr1QRhhshq6RgRidnOvTIWZKoe4QHQrvmOfW245zv+22Iuu5rYpcl ;{id = 53138 (ksk), size = 2048b}
gov.	86400	IN	DNSKEY	256 3 7 AQPCyrIcWu8PlnjEudjIIXHpefxjhkEHKel2I7CVrunY0/CkSBi+MTF+EbY8rsO0MxCcikdj2R6utTDj1l5noWnDmZIB0gJsW4xjUsRWGYrau/wRaVj2U8Je8nZs3KpduJj6aK2wTC+h0ggGqF+ucuPTOc0j3wIVX8P0PU3bQy48dKCHGd2YS+1rnQ5FQqlpJ9AXhVkAj3Y1vF6mW7GLrWnBryUbvl0uamrunB5888CfKMBsQgxQZHxeRhS/3PcaXUxHFE5XZDTx3qzuvHz3/3cdwpXfla6GRN8MfjFDRHMjFNrXu3PbVsjQqHXIzRBd8sS5RI5McJJcnprGEFdvj6Uv ;{id = 343 (zsk), size = 2048b}
sigs:
gov.	86399	IN	RRSIG	DNSKEY 7 1 86400 20130310220022 20130305220022 53138 gov. MHVmayoZ3dqYPF6JA9SxvJigw/opi8zTC+FDBVdPVpd3tB72DfNAozT2wIKuB6MI7p5RHRxKmzA+Jtc5yGBaFXU1A+3ybf24pgK4ZPnNERTs28xLm+mwc+FRaFPA9ArpFFUOKh4g7lFnLQb3ysexF+dGoyikL6kl5PiYwM6DBRRMzOR5P8bcQ2dKSd9G/DVxHWqWe4knun6glLg6wjA+0g4d4CLEcfHyzBSNc/4UMQ4ubC/2UDQDYezh4ufcPP3TGE2yUFcuD6aAdQ+KQNSA2lw3hxjX35sZJ5/uovnt7MoMKl0MSAUw3xtazGyxb3cu7yk/2rEPhW7Nq8d8tQmyyg==
---
;; rcode: NOERROR
;; qtype: DS
rrset:
fbi.gov.	86400	IN	DS	24840 7 1 1a587e6ffaf669448d6cef00403e3b91a9b33916
fbi.gov.	86400	IN	DS	24840 7 2 0c31ebaed7f6a22619eadd082417ab38fa4b4af871fd6507f040cd916b098d18
sigs:
fbi.gov.	86400	IN	RRSIG	DS 7 2 86400 20130310220022 20130305220022 343 gov. CIviEGPF2cTo/DxRK1oDIVae2hoUWQf22MYh7qh5GHSuHcBzbSAqzDuviVgdK/hz6DVV5ufIbx2ScyMKHJ6zHzzsGpBuSCuLo88kn7Gx+OYQzW1rpy7P1wImocCmCe53Kh5W38rxwFUoZNynUki+Io4B9MLqScUGbcvD6aqcKL6k9Mmx2z219nynqcbJWV1uSiemAf0EzcIOB69deTbIU5XVlqEuGf/CQjIBgmhkYNWsWv9d7b63OX5e6ZbjyDiDHteFtivVvAecwU3BIjKMpAXrkYIchZyMmzDPnaVYSYqppbD4u8FWgaQg6IGUaBUEyMeIfAURwjbUzR+R/g9+uQ==
---
;; rcode: NOERROR
;; qtype: DNSKEY
rrset:
fbi.gov.	600	IN	DNSKEY	256 3 7 BQEAAAABo4psWp89WZYhcyU1e7HiJgURDcNSPRJigtcKjUZq+zm3smS++eQyjVDZQOWsQxyyCw/HF1sT/goY2VO7Nm6uQ7y/kxgGeTkTiQAkcJ9GEI30RHaWrdMlmFuMLHV0Hdf9OxuXqAxLdEjq4UcVz0C/L5y6KECIlrFwFA/PPsdbpZc= ;{id = 32497 (zsk), size = 1024b}
fbi.gov.	600	IN	DNSKEY	256 3 7 BQEAAAAB17UX5M/RKhkRgfUM4GYr+wCTTfLpe232895mX0GH/3R2SnYFTTCEPF7hNF5nkt6yW57fs1wt8/FrdQom7lRLZhgaZdXHGNSbLraq8jMAq9CmNvoNzhoiXbOUdwf2Hw2zcrozYgAoEfxeX0cCf5je4DSRkwEHZ7L+t2y15M9WwZk= ;{id = 58969 (zsk), size = 1024b}
fbi.gov.	600	IN	DNSKEY	257 3 7 AwEAAcbqigwPaVWRtu5tXoSIHRnjafvgHIKVo/I1nWZpCgCgGEwy6AZ4+OxktFgaVtVEIqNyeeCM9pkjly1isnwZDcWRHbzwmJ3dgKfnml8c5GIJnPp+4NcUHh8YzV+NAurNxaOWp7VDgJRuUejkyKNStia8B4WgcHK26ztGjy6wA/lkVUmea0H/EawqxrolACAD44kYjSpHxTx2dLeoqLfA4BR38aVCT8QTR6jb0Prt2x3v5bGxsW8nv9EvYZOYJHxzhZ6qoPKTCSFpXbPJvJRe/OQpIM+oANQzqPJtnnXNQqa72bJz4xZ4ybZo5tDbqEbY9i/i1KfZxxin01tz1Sk8o8M= ;{id = 24840 (ksk), size = 2048b}
fbi.gov.	600	IN	DNSKEY	257 3 7 AwEAAco9GtgN9u27gk77N3mrGDJ/ifCuPjJVba6bNnEqcamqf/Zhz5ysspP2LuQN2Grn1neWPLNZxi/fIzQDw+r3fUw8++W28AXt4nH+7J3vmySBX+kEwCXuzhigxXWHnh6TawVDmKFHAh/VOqFjXVRvOBW18S4PJ+ee+AwOtQh60tNuPNBVQvNkuOrG6q1o1OnLYyP9dKkcEK7FwH6lo11qNhwq8z6VFgQV7Kc1RxPiKEI/22GCFlzzyqTdN3DGbwiwIMcgVeJWvOBhQRRjoF/VPZ0eEDqQAG8mFamTcz7YU7J0fmhRKnJxEnr/dNcDYgibDOpW/ZIDiDD2JX9BzJgPV/U= ;{id = 60816 (ksk), size = 2048b}
sigs:
fbi.gov.	599	IN	RRSIG	DNSKEY 7 2 600 20130430205214 20130130205214 24840 fbi.gov. SHqan3CAHAn8SBP/XeKGRmS8Bza3W8N8a63IRT+rSxLfQu+XjgOfJ2KW5N6JsN4qoudiVW8zFLlEqlc1qH4kdu+tQYcnLnFILfZ4QijHu5i+E0RfqOSurCmcgdd+b+gNBBgbnjPYjNUnyOgcHg3fsBsgl2594YE0T715xELXspmw7e8UHJmWnDCOY7EMKPwDlJTuHsYr10uKXyCQPnuGG4J4HOI4wAhaxCYUo97pqE0eoi/VCYP6VA1QdkvlbOqHo6C+mrdbSESN3AP0q97ZSgpejBXjqy37vTmrwK0H9ThslqC/LKtKwr8+IsuabqQC8TlCdGZDjMjsfZrOwfEqCQ==
fbi.gov.	599	IN	RRSIG	DNSKEY 7 2 600 20130430205214 20130130205214 32497 fbi.gov. EY6sw9FCzcBHqfZv67lZgoWu3OEvJlMFCTvuKIi8GcuAI9pU0GwwClD/tYgSpBNQVY56GBQorEkXh2EpKNZMsbLL9U1Pvp+cAS8RlhGuzZWdUsUntxK42iMDDqaSdfOMmnP5QUjQ5+hGY2+scl9Ls/4rLMsG0umGb2oHVOmi6wE=
---
;; rcode: NOERROR
rrset:
fbi.gov.	600	IN	A	72.21.81.85
sigs:
fbi.gov.	600	IN	RRSIG	A 7 2 600 20130430205214 20130130205214 32497 fbi.gov. B/2hm6w2dQH6votIFLWTgGC6G2yJb7NuAfLuaGkIKdqZsTCo2NEYbGm8ugrxrU6cgIInnWlDszL1KTgjR63YE79MMccOtysVkCP5P8fGbIdApNLjmTkSQxusW/XgB+prd4cujpphKjyDQ1F3QIgtjKJOvVzQoTcpdhl8W6OwSUU=
---
```

