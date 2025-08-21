# libcurl-psp2
Relatively small libcurl port for PSP2 as single .suprx module with 0 external dependencies.

No source is provided since in order to achieve 0 external dependencies this module was built with an unholy abomination of VitaSDK and official SCE SDK which no one will be able to replicate without loosing their sanity in the process.

# Versions

| Library  | Version |
| ------------- | ------------- |
| curl  | 8.15.0  |
| mbedtls  | 3.6.4  |
| libpsl  | 0.21.5 |

libcurl is built with the following config (only values relevant to usage shown):

```-DENABLE_IPV6=OFF -DCURL_DISABLE_SOCKETPAIR=ON -DHAVE_FCNTL_O_NONBLOCK=OFF -DENABLE_THREADED_RESOLVER=OFF -DCURL_CA_BUNDLE="vs0:data/external/cert/CA_LIST.cer" -DCURL_USE_MBEDTLS=ON  DCURL_USE_OPENSSL=OFF -DHAVE_POLL_FINE=1```

# Usage

Load module as usual. Before using any other functions, set memory allocators with:

```typedef void*(*curl_allocate)(unsigned int);
typedef void(*curl_free)(void *);
typedef void*(*curl_reallocate)(void *, unsigned int);

int curl_global_memmanager_set_np(curl_allocate, curl_free, curl_reallocate);
