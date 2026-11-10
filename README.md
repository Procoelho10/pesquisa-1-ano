<!DOCTYPE html>
<html lang="pt-BR" class="h-full bg-slate-50"><head><script data-bard-client-injected="true">(function(firebaseConfig, initialAuthToken, appId) {
        window.__firebase_config = firebaseConfig;
        window.__initial_auth_token = initialAuthToken;
        window.__app_id = appId;
            })("\n{\n  \"apiKey\": \"AIzaSyCqyCcs2R2e7AegGjvFAwG98wlamtbHvZY\",\n  \"authDomain\": \"bard-frontend.firebaseapp.com\",\n  \"projectId\": \"bard-frontend\",\n  \"storageBucket\": \"bard-frontend.firebasestorage.app\",\n  \"messagingSenderId\": \"175205271074\",\n  \"appId\": \"1:175205271074:web:2b7bd4d34d33bf38e6ec7b\"\n}\n","eyJhbGciOiJSUzI1NiIsImtpZCI6IjExNjRiNzdiNDMzZDdhMDAyMWI4NjE4YjhjYTU3ZTMyZGI5MWUxMTMiLCJ0eXAiOiJKV1QifQ.eyJzdWIiOiJmaXJlYmFzZS1hZG1pbnNkay1mYnN2Y0BiYXJkLWZyb250ZW5kLmlhbS5nc2VydmljZWFjY291bnQuY29tIiwiYXVkIjoiaHR0cHM6Ly9pZGVudGl0eXRvb2xraXQuZ29vZ2xlYXBpcy5jb20vZ29vZ2xlLmlkZW50aXR5LmlkZW50aXR5dG9vbGtpdC52MS5JZGVudGl0eVRvb2xraXQiLCJ1aWQiOiIwNTQ3Mjc0MDQ2MDM3ODkxOTcwNyIsImlzcyI6ImZpcmViYXNlLWFkbWluc2RrLWZic3ZjQGJhcmQtZnJvbnRlbmQuaWFtLmdzZXJ2aWNlYWNjb3VudC5jb20iLCJjbGFpbXMiOnsiYXBwSWQiOiJjXzllNWYwN2Q0YzU5ZDgyYzFfaW5kZXguaHRtbC03MjMifSwiZXhwIjoxNzk0MzI1Njg1LCJpYXQiOjE3OTQzMjIwODUsImFsZyI6IlJTMjU2In0.J_0FKuzbF2vtYx1QO400oCxou4TOsR5T2D7I24Z37aZF7SFUm42-t32CRt0ZMO0nqpTJjppvEq6NqMgZW8IZA6-RDihsG_0S4WNXMjAkV2q04l_ZAiBNwoyQyx_sSZALBfzfqFKGF9NylGUsakJ0qijw0Rf4rTYGUluo1tdZ8sj8vy7fuZMNRc3S1883kmb22udvIJR-D1ZevdmRvBXLRgl5EBT0QD-g-t6_QOFqwM6QvilwrwPAt2GpgIo1iyy62Owli_yePXfWOHDJZ9Mj0L0qU_1TU76icyY4xGOtxfmRU6U-TE6lr19FD7-oTkKnjS4GE6DszY9kfPuvTVz0ng","c_9e5f07d4c59d82c1_index.html-723")</script><script data-bard-client-injected="true">
  document.addEventListener('input', (event) => {
    if (event.target && (event.target.isContentEditable || event.target.hasAttribute('contenteditable'))) {
      const clonedDoc = document.cloneNode(true);
      const injectedScripts = clonedDoc.querySelectorAll('[data-bard-client-injected="true"]');
      injectedScripts.forEach(el => el.remove());
      window.parent.postMessage({
        type: 'inlineEdit',
        html: '<!DOCTYPE html>\n' + clonedDoc.documentElement.outerHTML
      }, '*');
    }
  });
</script><script data-bard-client-injected="true">(function(){'use strict';window.addEventListener("message",a=>{a.data&&a.data.type==="SUPPLEMENTAL_DATA_UPDATE"&&window.dispatchEvent(new CustomEvent("supplementaldataupdate",{detail:a.data.data}))});}).call(this);
</script><script data-bard-client-injected="true">(function() {
  const SCROLL_KEYS = new Set([
    'ArrowUp', 'ArrowDown', 'ArrowLeft', 'ArrowRight',
    ' ', 'Spacebar', 'PageUp', 'PageDown', 'Home', 'End',
  ]);
  const HORIZONTAL_KEYS = new Set(['ArrowLeft', 'ArrowRight']);

  function isTextEntryTarget(target) {
    if (!target) return false;
    const tagName = target.tagName;
    return tagName === 'INPUT' || tagName === 'TEXTAREA' ||
        tagName === 'SELECT' || target.isContentEditable === true;
  }

  // An element absorbs the key only if it both overflows on the axis being
  // scrolled and is configured to scroll on that axis. The cheap dimension
  // test runs first because getComputedStyle forces a style recalc, and this
  // runs on every keypress. Each axis is read from its own longhand: the
  // 'overflow' shorthand serializes as two values when the axes differ, which
  // is the common 'overflow-x: hidden; overflow-y: auto' pane.
  function canScroll(node, horizontal) {
    const overflows = horizontal ? node.scrollWidth > node.clientWidth
                                 : node.scrollHeight > node.clientHeight;
    if (!overflows) return false;
    const style = window.getComputedStyle(node);
    const overflow = horizontal ? style.overflowX : style.overflowY;
    return overflow === 'auto' || overflow === 'scroll';
  }

  // Walks up from the event target so nested scrollers keep their behavior.
  // <body> is included because pages that pin the root height make it the
  // scroll container.
  function hasScrollableAncestor(target, horizontal) {
    let node = target;
    while (node && node !== document.documentElement) {
      if (canScroll(node, horizontal)) return true;
      node = node.parentElement;
    }
    return false;
  }

  function rootCanScroll(horizontal) {
    const scroller = document.scrollingElement || document.documentElement;
    if (!scroller) return false;
    // Tolerate a pixel of rounding so subpixel layouts do not look scrollable.
    return horizontal ? scroller.scrollWidth > window.innerWidth + 1
                      : scroller.scrollHeight > window.innerHeight + 1;
  }

  window.addEventListener('keydown', function(event) {
    if (!SCROLL_KEYS.has(event.key)) return;
    if (event.defaultPrevented) return;
    // Alt and Meta turn arrows into browser history navigation, and Ctrl is
    // reserved for shortcuts, so none of them are scroll intent.
    if (event.altKey || event.metaKey || event.ctrlKey) return;

    const target = event.target;
    if (isTextEntryTarget(target)) return;

    // Anything that can still absorb the scroll gets to keep it.
    const horizontal = HORIZONTAL_KEYS.has(event.key);
    if (rootCanScroll(horizontal)) return;
    if (hasScrollableAncestor(target, horizontal)) return;

    event.preventDefault();
  }, {capture: true, passive: false});
})();</script><script data-bard-client-injected="true">(function() {
  // Ensure this script is executed only once
  if (window.firebaseAuthBridgeScriptLoaded) {
    return;
  }
  window.firebaseAuthBridgeScriptLoaded = true;

  let nextTokenPromiseId = 0;

  // Stores { resolve, reject } for ongoing token requests
  const pendingTokenPromises = {};

  // Listen for messages from the Host Application
  window.addEventListener('message', function(event) {

    const messageData = event.data;

  if (messageData && messageData.type === 'RESOLVE_NEW_FIREBASE_TOKEN') {
      const { success, token, error, promiseId } = messageData ?? {};
      if (pendingTokenPromises[promiseId]) {
        if (success) {
          pendingTokenPromises[promiseId].resolve(token);
        } else {
          pendingTokenPromises[promiseId].reject(new Error(error || 'Token refresh failed from host.'));
        }
        delete pendingTokenPromises[promiseId];
      }
    }
  });

  // Expose a function for the Generated App to request a new Firebase token
  window.requestNewFirebaseToken = function() {
    const currentPromiseId = nextTokenPromiseId++;
    const promise = new Promise((resolve, reject) => {
      pendingTokenPromises[currentPromiseId] = { resolve, reject };
    });
    if (window.parent && window.parent !== window) {
      window.parent.postMessage({
        type: 'REQUEST_NEW_FIREBASE_TOKEN',
        promiseId: currentPromiseId
      }, '*');
    } else {
      pendingTokenPromises[currentPromiseId].reject(new Error('No parent window to request token from.'));
      delete pendingTokenPromises[currentPromiseId];
    }
    return promise;
  };
})();</script><script data-bard-client-injected="true">
let realOriginalGetUserMedia = null;
if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
  realOriginalGetUserMedia = navigator.mediaDevices.getUserMedia.bind(navigator.mediaDevices);
}

(function() {
  if (navigator.mediaDevices && navigator.mediaDevices.__proto__) {
    try {
      Object.defineProperty(navigator.mediaDevices.__proto__, 'getUserMedia', {
        get: function() {
          return undefined; // Or throw an error
        },
        configurable: false
      });
    } catch (error) {
      console.error("Error defining prototype getter:", error);
    }
  }
})();

(function() {
  const pendingMediaResolvers = {};
  let nextMediaPromiseId = 0;

  function requestMediaPermissions(constraints) {
    const mediaPromiseId = nextMediaPromiseId++;
    const promise = new Promise((resolve, reject) => {
      pendingMediaResolvers[mediaPromiseId] = (granted) => {
        delete pendingMediaResolvers[mediaPromiseId];
        resolve(granted);
      };
    });

    window.parent.postMessage({
      type: 'requestMediaPermission',
      constraints: constraints,
      promiseId: mediaPromiseId,
    }, '*');

    return promise;
  }

  let originalGetUserMedia = realOriginalGetUserMedia;

  function interceptGetUserMedia() {
    if (navigator.mediaDevices) {
      Object.defineProperty(navigator.mediaDevices, 'getUserMedia', {
        value: function(constraints) {
          return requestMediaPermissions(constraints).then((granted) => {
            if (granted) {
              if (originalGetUserMedia) {
                return originalGetUserMedia(constraints);
              } else {
                throw new Error("Original getUserMedia not available.");
              }
            } else {
              throw new DOMException('Permission denied', 'NotAllowedError');
            }
          });
        },
        writable: false,
        configurable: false
      });
    }
  }

  interceptGetUserMedia();

  const observer = new MutationObserver(function(mutationsList, observer) {
    for (const mutation of mutationsList) {
      if (mutation.type === 'reconfigured' && mutation.name === 'getUserMedia' && mutation.object === navigator.mediaDevices) {
        interceptGetUserMedia();
      } else if (mutation.type === 'attributes' && mutation.attributeName === 'getUserMedia' && mutation.target === navigator.mediaDevices) {
        interceptGetUserMedia();
      } else if (mutation.type === 'childList' && mutation.addedNodes) {
        mutation.addedNodes.forEach(node => {
          if (node === navigator.mediaDevices) {
            interceptGetUserMedia();
          }
        });
      }
    }
  });

  function interceptSpeechRecognition() {
    if (!window.SpeechRecognition && !window.webkitSpeechRecognition) {
      return;
    }

    const OriginalSpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

    const SpeechRecognitionWrapper = function(...args) {
      const recognizer = new OriginalSpeechRecognition(...args);
      const originalStart = recognizer.start.bind(recognizer);

      recognizer.start = function() {
        requestMediaPermissions({ audio: true }).then(granted => {
          if (granted) {
            originalStart();
          } else {
            const errorEvent = new SpeechRecognitionErrorEvent('error');
            errorEvent.error = 'not-allowed'; // This is the standard error for permission denial.
            recognizer.dispatchEvent(errorEvent);
          }
        });
      };

      return recognizer;
    };

    SpeechRecognitionWrapper.prototype = OriginalSpeechRecognition.prototype;
    SpeechRecognitionWrapper.prototype.constructor = SpeechRecognitionWrapper;

    if (window.SpeechRecognition) {
      window.SpeechRecognition = SpeechRecognitionWrapper;
    }
    if (window.webkitSpeechRecognition) {
      window.webkitSpeechRecognition = SpeechRecognitionWrapper;
    }
  }

  interceptSpeechRecognition();

  window.addEventListener('message', function(event) {
    if (event.data) {
      if (event.data.type === 'resolveMediaPermission') {
        const { promiseId, granted } = event.data;
        if (pendingMediaResolvers[promiseId]) {
          pendingMediaResolvers[promiseId](granted);
        }
      }
    }
  });

})();</script><script ws-interception-config="{&quot;parentOrigin&quot;:&quot;https://gemini.google.com&quot;,&quot;proxiedDomains&quot;:[]}" data-bard-client-injected="true">(function(){'use strict';var u=typeof Object.defineProperties=="function"?Object.defineProperty:function(b,d,e){if(b==Array.prototype||b==Object.prototype)return b;b[d]=e.value;return b};function v(b){b=["object"==typeof globalThis&&globalThis,b,"object"==typeof window&&window,"object"==typeof self&&self,"object"==typeof global&&global];for(var d=0;d<b.length;++d){var e=b[d];if(e&&e.Math==Math)return e}throw Error("Cannot find global object");}var w=v(this);
function y(b,d){if(d)a:{var e=w;b=b.split(".");for(var h=0;h<b.length-1;h++){var k=b[h];if(!(k in e))break a;e=e[k]}b=b[b.length-1];h=e[b];d=d(h);d!=h&&d!=null&&u(e,b,{configurable:!0,writable:!0,value:d})}}function z(b){function d(h){return b.next(h)}function e(h){return b.throw(h)}return new Promise(function(h,k){function m(n){n.done?h(n.value):Promise.resolve(n.value).then(d,e).then(m,k)}m(b.next())})}y("globalThis",function(b){return b||w});/*

 Copyright The Closure Library Authors.
 SPDX-License-Identifier: Apache-2.0
*/
function A(b,d){function e(){}e.prototype=d.prototype;b.j=d.prototype;b.prototype=new e;b.prototype.constructor=b;b.h=function(h,k,m){for(var n=Array(arguments.length-2),p=2;p<arguments.length;p++)n[p-2]=arguments[p];return d.prototype[k].apply(h,n)}};function B(b,d,e="*"){function h(a){if(typeof a==="string")return F.encode(a).buffer;if(a instanceof ArrayBuffer)return a.slice(0);if(ArrayBuffer.isView(a))return a.buffer.slice(a.byteOffset,a.byteOffset+a.byteLength);throw Error("Invalid data type");}function k(a){a=h(a);var f={type:"send",data:new Uint8Array(a)},g;(g=r)==null||g.postMessage(f,[a])}function m(){if(!r)throw Error("Data port not captured yet.");r.onmessage=a=>{if(a.data.type==="message"){a=new MessageEvent("message",{data:G.decode(a.data.data)});
let f;(f=c.onmessage)==null||f.call(c,a);c.dispatchEvent(a)}}}function n(){if(!t)throw Error("Control port not captured yet.");t.onmessage=a=>{switch(a.data.type){case "open":l=1;var f=new Event("open"),g;(g=c.onopen)==null||g.call(c,f);c.dispatchEvent(f);q.forEach(H=>{k(H)});q=[];break;case "close":g=a.data;l=3;g=new CloseEvent("close",{code:g.code,reason:g.reason,wasClean:g.wasClean});(f=c.onclose)==null||f.call(c,g);c.dispatchEvent(g);break;case "error":l=3;f=new Event("error");let x;(x=c.onerror)==
null||x.call(c,f);c.dispatchEvent(f)}}}function p(a){return z(function*(){var f=new MessageChannel;t=f.port1;var g=new MessageChannel;r=g.port1;n();m();window.parent.postMessage({type:"websocket_open",portOrdering:["control","data"],url:b,protocols:a||[],connectionId:I},e,[f.port2,g.port2])}())}var c=Reflect.construct(EventTarget,[],new.target);c.CONNECTING=0;c.OPEN=1;c.CLOSING=2;c.CLOSED=3;c.url=b;c.binaryType="arraybuffer";c.protocol="";c.i="";var l=0,t=null,r=null,q=[],F=new TextEncoder,G=new TextDecoder;
c.onopen=null;c.onmessage=null;c.onclose=null;c.onerror=null;Object.defineProperty(c,"readyState",{get:()=>l,enumerable:!0,configurable:!0});Object.defineProperty(c,"bufferedAmount",{get:()=>{var a=0;q.forEach(f=>{a+=typeof f==="string"?f.length:f.byteLength});return a},enumerable:!0,configurable:!0});var I=function(){var a;return((a=globalThis.crypto)==null?0:a.randomUUID)?globalThis.crypto.randomUUID():"xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx".replace(/[xy]/g,f=>{var g=Math.random()*16|0;return(f===
"x"?g:g&3|8).toString(16)})}();c.send=a=>{if(l===1)a instanceof Blob?a.arrayBuffer().then(f=>{k(f)}):k(a);else if(l===0)if(typeof a==="string")q.push(a);else if(a instanceof ArrayBuffer||ArrayBuffer.isView(a))q.push(h(a));else throw Error("Sending Blob is not supported before the connection is open.");else console.debug("WebSocket send called in CLOSING or CLOSED state; ignored.")};c.close=(a=1E3,f="")=>{if(l!==2&&l!==3){l=2;a={type:"close",code:a,reason:f,wasClean:a===1E3};var g;(g=t)==null||g.postMessage(a)}};
Promise.resolve().then(()=>p(d));return c}A(B,EventTarget);var C=document.currentScript,D=C==null?void 0:C.getAttribute("ws-interception-config");if(!D)throw Error("WebSocket Interceptor: Missing ws-interception-config attribute in the script tag.");var E=JSON.parse(D);if(!E.parentOrigin||typeof E.parentOrigin!=="string")throw Error("WebSocket Interceptor: Invalid parentOrigin in ws-interception-config");
(function(b){var d=Object.getOwnPropertyDescriptor(window,"WebSocket");if(!d||d.writable||d.configurable)d=Object.assign(function(e,h){try{let k=(new URL(e)).hostname;if(b.proxiedDomains.some(m=>k===m||k.endsWith(`.${m}`)))return new B(e,h,b.parentOrigin)}catch(k){throw window.parent.postMessage({type:"websocket_blocked",url:e,reason:"blocked_invalid_url"},b.parentOrigin),new DOMException(`WebSocket connection to '${e}' is not allowed in Canvas.`,"SecurityError");}window.parent.postMessage({type:"websocket_blocked",
url:e,reason:"blocked_domain_not_allowlisted"},b.parentOrigin);throw new DOMException(`WebSocket connection to '${e}' is not allowed in Canvas.`,"SecurityError");},{CONNECTING:0,OPEN:1,CLOSING:2,CLOSED:3}),Object.defineProperty(window,"WebSocket",{value:d,writable:!1,configurable:!1})})({proxiedDomains:E.proxiedDomains||[],parentOrigin:E.parentOrigin});}).call(this);
</script><script data-bard-client-injected="true">((function(modelInformation) {
  const originalFetch = window.fetch;
  // TODO: b/421908508 - Move these out of the script and match all generative AI model calls.
  let googleLlmBaseApiUrls = [
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.textModelName + ':streamGenerateContent',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.textModelName + ':generateContent',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.imageModelName + ':predict',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.imageModelName + ':predictLongRunning',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.imageEditModelName + ':generateContent',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.imageTransformModelName + ':generateContent',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.videoModelName + ':predict',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.videoModelName + ':predictLongRunning',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.ttsModelName + ':generateContent',
  ];
  modelInformation.deprecatedTextModelNames.forEach((modelName) => {
    googleLlmBaseApiUrls.push(
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':streamGenerateContent',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':generateContent',
    );
  });
  modelInformation.deprecatedImageModelNames.forEach((modelName) => {
    googleLlmBaseApiUrls.push(
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':predict',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':predictLongRunning',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':generateContent',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':streamGenerateContent',
    );
  });
  modelInformation.deprecatedGenerateImageModelNames.forEach((modelName) => {
    googleLlmBaseApiUrls.push(
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':generateContent',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':streamGenerateContent',
    );
  });
  modelInformation.deprecatedImageTransformModelNames.forEach((modelName) => {
    googleLlmBaseApiUrls.push(
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':generateContent',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':streamGenerateContent',
    );
  });

  const pendingFetchResolvers = {};
  let nextPromiseId = 0;

  function handleStringInput(input, optionsArgument) {
    const actualUrl = input;
    const fetchCallArgs = [actualUrl, optionsArgument];
    const effectiveOptions = optionsArgument || {};
    const bodyForApiKeyCheck = effectiveOptions.body;
    const bodyForPostMessage = effectiveOptions.body;
    return { actualUrl, fetchCallArgs, effectiveOptions, bodyForApiKeyCheck, bodyForPostMessage };
  }

  function handleRequestInput(input, optionsArgument) {
    const actualUrl = input.url;
    const fetchCallArgs = [input, optionsArgument];
    const effectiveOptions = { method: input.method, headers: new Headers(input.headers) };
    let bodyForApiKeyCheck;
    let bodyForPostMessage;

    if (optionsArgument) {
      if (optionsArgument.method) effectiveOptions.method = optionsArgument.method;
      if (optionsArgument.headers) effectiveOptions.headers = new Headers(optionsArgument.headers);
      if ('body' in optionsArgument) {
        bodyForApiKeyCheck = optionsArgument.body;
        bodyForPostMessage = optionsArgument.body;
      } else {
        bodyForApiKeyCheck = undefined;
        bodyForPostMessage = input.body;
      }
    } else {
      bodyForApiKeyCheck = undefined;
      bodyForPostMessage = input.body;
    }
    return { actualUrl, fetchCallArgs, effectiveOptions, bodyForApiKeyCheck, bodyForPostMessage };
  }

  window.fetch = function(input, optionsArgument) {
    let actualUrl;
    let fetchCallArgs;
    let effectiveOptions = {};
    let bodyForApiKeyCheck;
    let bodyForPostMessage;

    if (typeof input === 'string') {
      ({actualUrl, fetchCallArgs, effectiveOptions, bodyForApiKeyCheck, bodyForPostMessage} = handleStringInput(input, optionsArgument));
    } else if (input instanceof Request) {
      ({actualUrl, fetchCallArgs, effectiveOptions, bodyForApiKeyCheck, bodyForPostMessage} = handleRequestInput(input, optionsArgument));
    } else {
      return originalFetch.apply(window, [input, optionsArgument]);
    }

    effectiveOptions.method = effectiveOptions.method || 'GET';
    if (!effectiveOptions.headers) {
      effectiveOptions.headers = new Headers();
    }


    if (typeof actualUrl === 'string' && googleLlmBaseApiUrls.some((url) => actualUrl.startsWith(url))) {
      let apiKeyIsNull = true;

      const regex = new RegExp("models/([^:]+)");
      const modelNameMatch = actualUrl.match(regex);
      const modelName = modelNameMatch ? modelNameMatch[1] : 'unspecified';


      try {
        const urlObject = new URL(actualUrl);  // Use URL object for robust parsing
        const apiKeyParam = urlObject.searchParams.get('key');
        if (apiKeyParam) {
          apiKeyIsNull = false;
        }
      } catch (e) {
        // Continue checks even if URL parsing fails
      }

      if (apiKeyIsNull && effectiveOptions.headers) {
        const h = new Headers(effectiveOptions.headers);
        const apiKeyHeaderValue = h.get('X-API-Key') || h.get('x-api-key');
        if (apiKeyHeaderValue) {
          apiKeyIsNull = false;
          return originalFetch.apply(window, fetchCallArgs);
        }
      }

      if (apiKeyIsNull && effectiveOptions.method && ['POST', 'PUT', 'PATCH'].includes(effectiveOptions.method.toUpperCase()) && typeof bodyForApiKeyCheck === 'string') {
        try {
          const bodyData = JSON.parse(bodyForApiKeyCheck);
          if (bodyData && bodyData.apiKey) {
            apiKeyIsNull = false;
            return originalFetch.apply(window, fetchCallArgs);
          }
        } catch (e) {
          // Ignore JSON parsing errors
        }
      }

      if(apiKeyIsNull) {
        const promiseId = nextPromiseId++;
        const promise = new Promise((resolve) => {
          pendingFetchResolvers[promiseId] = (resolvedResponse) => {
            delete pendingFetchResolvers[promiseId];
            resolve(resolvedResponse);
          };
        });

        let serializedBodyForPostMessage;
        if (typeof bodyForPostMessage === 'string' || bodyForPostMessage == null) {
            serializedBodyForPostMessage = bodyForPostMessage;
        } else if (bodyForPostMessage instanceof ReadableStream) {
            serializedBodyForPostMessage = null;
        } else {
            try {
                serializedBodyForPostMessage = JSON.stringify(bodyForPostMessage);
            } catch (e) {
                serializedBodyForPostMessage = null;
            }
        }

        const messageOptions = {
            method: effectiveOptions.method,
            headers: Object.fromEntries(new Headers(effectiveOptions.headers).entries()),
            body: serializedBodyForPostMessage
        };

        window.parent.postMessage({
          type: 'requestFetch',
          url: actualUrl,
          modelName: modelName,
          options: messageOptions,
          promiseId: promiseId,
        }, '*');

        return promise;
      }
      return originalFetch.apply(window, fetchCallArgs);
    }
    return originalFetch.apply(window, fetchCallArgs);
  };

  window.addEventListener('message', function(event) {
    if (event.data && event.data.type === 'resolveFetch') {
      const { promiseId, response } = event.data;
      if (pendingFetchResolvers[promiseId]) {
        try {
          const reconstructedResponse = new Response(response.body, {
            status: response.status,
            statusText: response.statusText,
            headers: new Headers(response.headers),
          });
          pendingFetchResolvers[promiseId](reconstructedResponse);
        } catch (error) {
          pendingFetchResolvers[promiseId](new Response(null, { status: 500, statusText: "Interceptor Response Reconstruction Error" }));
        }
      }
    }
  });

}))({"textModelName":"gemini-3-flash-preview","imageModelName":"imagen-4.0-generate-001","imageEditModelName":"gemini-3.1-flash-image","imageTransformModelName":"gemini-3-pro-image","videoModelName":"veo-2.0-generate-001","ttsModelName":"gemini-2.5-flash-preview-tts","deprecatedTextModelNames":["gemini-2.0-flash","gemini-2.5-flash","gemini-2.5-flash-preview-04-17","gemini-2.5-flash-preview-05-20","gemini-2.5-flash-preview-09-2025"],"deprecatedImageModelNames":["imagen-3.0-generate-001","imagen-3.0-generate-002"],"deprecatedGenerateImageModelNames":["gemini-2.5-flash-image-preview","gemini-2.5-flash-image","gemini-3.1-flash-image-preview"],"deprecatedImageTransformModelNames":["gemini-3-pro-image-preview-11-2025"]})</script><script data-bard-client-injected="true">(function() {
  function normalizeSlug(str) {
    try {
      return str
        .trim()
        .toLowerCase()
        .replace(/[^p{L}p{N}s_-]/gu, '')
        .replace(/s+/g, '-');
    } catch (e) {
      return str
        .trim()
        .toLowerCase()
        .replace(/[^a-z0-9s_-]/g, '')
        .replace(/s+/g, '-');
    }
  }

  function findTargetElement(hash) {
    if (!hash || hash === '#') {
      return null;
    }
    const rawId = hash.startsWith('#') ? hash.slice(1) : hash;
    let decodedId = rawId;
    try {
      decodedId = decodeURIComponent(rawId);
    } catch (e) {
      // Ignore URI malformed errors.
    }

    // 1. Direct ID match (raw and decoded).
    let target = document.getElementById(rawId) || document.getElementById(decodedId);
    if (target) {
      return target;
    }

    // 2. Name attribute match (<a name="...">).
    try {
      if (typeof CSS !== 'undefined' && CSS.escape) {
        target =
          document.querySelector('[name="' + CSS.escape(rawId) + '"]') ||
          document.querySelector('[name="' + CSS.escape(decodedId) + '"]');
      } else {
        const namedElements = document.getElementsByName(rawId);
        if (namedElements && namedElements.length > 0) {
          return namedElements[0];
        }
      }
    } catch (e) {
      // Ignore querySelector syntax errors.
    }
    if (target) {
      return target;
    }

    // 3. Match heading text by slug (for Markdown TOCs where headings lack explicit IDs).
    const targetSlug = normalizeSlug(decodedId);
    if (targetSlug) {
      for (const heading of document.querySelectorAll('h1, h2, h3, h4, h5, h6')) {
        if (normalizeSlug(heading.textContent || '') === targetSlug) {
          return heading;
        }
      }
    }

    return null;
  }

  document.addEventListener('click', function(event) {
    const target = event.target;
    const anchor = target && typeof target.closest === 'function' ? target.closest('a') : null;
    if (!anchor) {
      return;
    }

    const href = anchor.getAttribute('href');
    if (
      !href ||
      href.trim().toLowerCase().startsWith('javascript:') ||
      anchor.hasAttribute('download')
    ) {
      return;
    }

    // Check if the link is an in-page hash / anchor link.
    if (href.startsWith('#')) {
      event.preventDefault();
      const targetElement = findTargetElement(href);
      if (targetElement) {
        targetElement.scrollIntoView({behavior: 'smooth', block: 'start'});
      }
      return;
    }

    // Check if the URL has the same origin/pathname but with a hash.
    try {
      const url = new URL(anchor.href, window.location.href);
      if (
        url.hash &&
        url.origin === window.location.origin &&
        url.pathname === window.location.pathname
      ) {
        event.preventDefault();
        const targetElement = findTargetElement(url.hash);
        if (targetElement) {
          targetElement.scrollIntoView({behavior: 'smooth', block: 'start'});
        }
        return;
      }
    } catch (e) {
      // Fall through if URL parsing fails.
    }

    // For all external or full navigation links, prevent iframe-level navigation
    // (which breaks in AGSA WebView or sandboxed iframes) and ensure they open
    // safely in a new tab/window.
    if (anchor.target !== '_blank') {
      event.preventDefault();
      window.open(anchor.href, '_blank', 'noopener,noreferrer');
    }
  }, {capture: true});
})();</script><script data-bard-client-injected="true">(function(){'use strict';function a(){window.parent.postMessage({type:"interaction"},"*")}window.addEventListener("click",a,{capture:!0,passive:!0});window.addEventListener("touchstart",a,{capture:!0,passive:!0});window.addEventListener("keydown",a,{capture:!0,passive:!0});}).call(this);
</script><script data-bard-client-injected="true">(function() {
  const originalConsoleLog = console.log;
  const originalConsoleError = console.error;

    /**
   * Normalizes an error event or a promise rejection reason into a structured error object.
   * @param {*} errorEventOrReason The error object or reason.
   * @return {object} Structured error data { message, name, stack }.
   */
  function getErrorObject(errorEventOrReason) {
    if (errorEventOrReason instanceof Error) {
      return {
        message: errorEventOrReason.message,
        name: errorEventOrReason.name,
        stack: errorEventOrReason.stack,
      };
    }
    // Fallback for non-Error objects.
    try {
      return {
        message: JSON.stringify(errorEventOrReason),
        name: 'UnknownErrorType',
        stack: null,
      };
    } catch (e) {
      return {
        message: String(errorEventOrReason),
        name: 'UnknownErrorTypeNonStringifiable',
        stack: null,
      };
    }
  }

  /**
   * Converts an array of arguments (from log/error) into a single string.
   * Handles Error objects specially to include their message and stack.
   * @param {Array<*>} args - Arguments passed to console methods.
   * @return {string} A string representation of the arguments.
   */
  function stringifyArgs(args) {
    return args
      .map((arg) => {
        if (arg instanceof Error) {
          const {message, stack} = arg;
          return `Error: ${message}${stack ? ('\nStack: ' + stack) : ''}`;
        }
        if (typeof arg === 'object' && arg !== null) {
          try {
            return JSON.stringify(arg);
          } catch (error) {
            return '[Circular Object]';
          }
        } else {
          return String(arg);
        }
      })
      .join(' ');
  }

  console.log = function(...args) {
    const logString = stringifyArgs(args);
    window.parent.postMessage({ type: 'log', message: logString }, '*');
    originalConsoleLog.apply(console, args);
  };

  console.error = function(...args) {
    let errorData;
    if (args.length > 0 && args[0] instanceof Error) {
      const err = args[0];
      // If the first arg is an Error, capture its details.
      errorData = {
        type: 'error',
        source: 'CONSOLE_ERROR',
        ...getErrorObject(err),
        rawArgsString: stringifyArgs(args.slice(1)),
        timestamp: new Date().toISOString(),
      };
    } else {
      // If not an Error object, treat all args as a general error message.
      errorData = {
        type: 'error',
        source: 'CONSOLE_ERROR',
        message: stringifyArgs(args),
        name: 'ConsoleLoggedError',
        stack: null,
        timestamp: new Date().toISOString(),
      };
    }
    window.parent.postMessage(errorData, '*');
    originalConsoleError.apply(console, args);
  };

  // Listen for global unhandled synchronous errors.
  window.addEventListener('error', function(event) {
    const errorDetails = event.error ? getErrorObject(event.error) : {
      message: event.message,
      name: 'GlobalError',
      stack: null,
      filename: event.filename,
      lineno: event.lineno,
      colno: event.colno,
    };

    window.parent.postMessage({
      type: 'error',
      source: 'global',
      ...errorDetails,
      message: errorDetails.message || event.message,
      timestamp: new Date().toISOString(),
    }, '*');
  });

  // Listen for unhandled promise rejections (asynchronous errors).
  window.addEventListener('unhandledrejection', function(event) {
    const errorDetails = getErrorObject(event.reason);

    window.parent.postMessage({
      type: 'error',
      source: 'unhandledrejection',
      ...errorDetails,
      message: errorDetails.message || 'Unhandled Promise Rejection',
      timestamp: new Date().toISOString(),
    }, '*');
  });

})();</script>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pesquisa Teen (15-17 anos) - Análise Estatística Completa</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js CDN -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js" crossorigin="anonymous"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&amp;display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            50: '#f0f5ff',
                            100: '#e0ebff',
                            500: '#6366f1',
                            600: '#4f46e5',
                            700: '#4338ca',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
<style>*, ::before, ::after{--tw-border-spacing-x:0;--tw-border-spacing-y:0;--tw-translate-x:0;--tw-translate-y:0;--tw-rotate:0;--tw-skew-x:0;--tw-skew-y:0;--tw-scale-x:1;--tw-scale-y:1;--tw-pan-x: ;--tw-pan-y: ;--tw-pinch-zoom: ;--tw-scroll-snap-strictness:proximity;--tw-gradient-from-position: ;--tw-gradient-via-position: ;--tw-gradient-to-position: ;--tw-ordinal: ;--tw-slashed-zero: ;--tw-numeric-figure: ;--tw-numeric-spacing: ;--tw-numeric-fraction: ;--tw-ring-inset: ;--tw-ring-offset-width:0px;--tw-ring-offset-color:#fff;--tw-ring-color:rgb(59 130 246 / 0.5);--tw-ring-offset-shadow:0 0 #0000;--tw-ring-shadow:0 0 #0000;--tw-shadow:0 0 #0000;--tw-shadow-colored:0 0 #0000;--tw-blur: ;--tw-brightness: ;--tw-contrast: ;--tw-grayscale: ;--tw-hue-rotate: ;--tw-invert: ;--tw-saturate: ;--tw-sepia: ;--tw-drop-shadow: ;--tw-backdrop-blur: ;--tw-backdrop-brightness: ;--tw-backdrop-contrast: ;--tw-backdrop-grayscale: ;--tw-backdrop-hue-rotate: ;--tw-backdrop-invert: ;--tw-backdrop-opacity: ;--tw-backdrop-saturate: ;--tw-backdrop-sepia: ;--tw-contain-size: ;--tw-contain-layout: ;--tw-contain-paint: ;--tw-contain-style: }::backdrop{--tw-border-spacing-x:0;--tw-border-spacing-y:0;--tw-translate-x:0;--tw-translate-y:0;--tw-rotate:0;--tw-skew-x:0;--tw-skew-y:0;--tw-scale-x:1;--tw-scale-y:1;--tw-pan-x: ;--tw-pan-y: ;--tw-pinch-zoom: ;--tw-scroll-snap-strictness:proximity;--tw-gradient-from-position: ;--tw-gradient-via-position: ;--tw-gradient-to-position: ;--tw-ordinal: ;--tw-slashed-zero: ;--tw-numeric-figure: ;--tw-numeric-spacing: ;--tw-numeric-fraction: ;--tw-ring-inset: ;--tw-ring-offset-width:0px;--tw-ring-offset-color:#fff;--tw-ring-color:rgb(59 130 246 / 0.5);--tw-ring-offset-shadow:0 0 #0000;--tw-ring-shadow:0 0 #0000;--tw-shadow:0 0 #0000;--tw-shadow-colored:0 0 #0000;--tw-blur: ;--tw-brightness: ;--tw-contrast: ;--tw-grayscale: ;--tw-hue-rotate: ;--tw-invert: ;--tw-saturate: ;--tw-sepia: ;--tw-drop-shadow: ;--tw-backdrop-blur: ;--tw-backdrop-brightness: ;--tw-backdrop-contrast: ;--tw-backdrop-grayscale: ;--tw-backdrop-hue-rotate: ;--tw-backdrop-invert: ;--tw-backdrop-opacity: ;--tw-backdrop-saturate: ;--tw-backdrop-sepia: ;--tw-contain-size: ;--tw-contain-layout: ;--tw-contain-paint: ;--tw-contain-style: }/* ! tailwindcss v3.4.17 | MIT License | https://tailwindcss.com */*,::after,::before{box-sizing:border-box;border-width:0;border-style:solid;border-color:#e5e7eb}::after,::before{--tw-content:''}:host,html{line-height:1.5;-webkit-text-size-adjust:100%;-moz-tab-size:4;tab-size:4;font-family:Inter, sans-serif;font-feature-settings:normal;font-variation-settings:normal;-webkit-tap-highlight-color:transparent}body{margin:0;line-height:inherit}hr{height:0;color:inherit;border-top-width:1px}abbr:where([title]){-webkit-text-decoration:underline dotted;text-decoration:underline dotted}h1,h2,h3,h4,h5,h6{font-size:inherit;font-weight:inherit}a{color:inherit;text-decoration:inherit}b,strong{font-weight:bolder}code,kbd,pre,samp{font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;font-feature-settings:normal;font-variation-settings:normal;font-size:1em}small{font-size:80%}sub,sup{font-size:75%;line-height:0;position:relative;vertical-align:baseline}sub{bottom:-.25em}sup{top:-.5em}table{text-indent:0;border-color:inherit;border-collapse:collapse}button,input,optgroup,select,textarea{font-family:inherit;font-feature-settings:inherit;font-variation-settings:inherit;font-size:100%;font-weight:inherit;line-height:inherit;letter-spacing:inherit;color:inherit;margin:0;padding:0}button,select{text-transform:none}button,input:where([type=button]),input:where([type=reset]),input:where([type=submit]){-webkit-appearance:button;background-color:transparent;background-image:none}:-moz-focusring{outline:auto}:-moz-ui-invalid{box-shadow:none}progress{vertical-align:baseline}::-webkit-inner-spin-button,::-webkit-outer-spin-button{height:auto}[type=search]{-webkit-appearance:textfield;outline-offset:-2px}::-webkit-search-decoration{-webkit-appearance:none}::-webkit-file-upload-button{-webkit-appearance:button;font:inherit}summary{display:list-item}blockquote,dd,dl,figure,h1,h2,h3,h4,h5,h6,hr,p,pre{margin:0}fieldset{margin:0;padding:0}legend{padding:0}menu,ol,ul{list-style:none;margin:0;padding:0}dialog{padding:0}textarea{resize:vertical}input::placeholder,textarea::placeholder{opacity:1;color:#9ca3af}[role=button],button{cursor:pointer}:disabled{cursor:default}audio,canvas,embed,iframe,img,object,svg,video{display:block;vertical-align:middle}img,video{max-width:100%;height:auto}[hidden]:where(:not([hidden=until-found])){display:none}.fixed{position:fixed}.relative{position:relative}.sticky{position:sticky}.inset-0{inset:0px}.bottom-5{bottom:1.25rem}.right-5{right:1.25rem}.top-0{top:0px}.z-50{z-index:50}.mx-auto{margin-left:auto;margin-right:auto}.mb-6{margin-bottom:1.5rem}.mt-0\.5{margin-top:0.125rem}.mt-1{margin-top:0.25rem}.mt-2{margin-top:0.5rem}.mb-1{margin-bottom:0.25rem}.mb-2{margin-bottom:0.5rem}.block{display:block}.flex{display:flex}.grid{display:grid}.hidden{display:none}.h-full{height:100%}.h-16{height:4rem}.h-2\.5{height:0.625rem}.h-8{height:2rem}.h-28{height:7rem}.h-64{height:16rem}.min-h-\[260px\]{min-height:260px}.w-2\.5{width:0.625rem}.w-8{width:2rem}.w-full{width:100%}.w-28{width:7rem}.w-32{width:8rem}.w-36{width:9rem}.max-w-4xl{max-width:56rem}.max-w-7xl{max-width:80rem}.max-w-lg{max-width:32rem}.flex-1{flex:1 1 0%}.flex-shrink-0{flex-shrink:0}.translate-y-2{--tw-translate-y:0.5rem;transform:translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.transform{transform:translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}@keyframes pulse{50%{opacity:.5}}.animate-pulse{animation:pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite}.cursor-pointer{cursor:pointer}.grid-cols-1{grid-template-columns:repeat(1, minmax(0, 1fr))}.grid-cols-2{grid-template-columns:repeat(2, minmax(0, 1fr))}.flex-col{flex-direction:column}.flex-wrap{flex-wrap:wrap}.items-start{align-items:flex-start}.items-center{align-items:center}.justify-end{justify-content:flex-end}.justify-center{justify-content:center}.justify-between{justify-content:space-between}.gap-1{gap:0.25rem}.gap-2{gap:0.5rem}.gap-3{gap:0.75rem}.gap-4{gap:1rem}.gap-6{gap:1.5rem}.space-x-1 > :not([hidden]) ~ :not([hidden]){--tw-space-x-reverse:0;margin-right:calc(0.25rem * var(--tw-space-x-reverse));margin-left:calc(0.25rem * calc(1 - var(--tw-space-x-reverse)))}.space-x-2 > :not([hidden]) ~ :not([hidden]){--tw-space-x-reverse:0;margin-right:calc(0.5rem * var(--tw-space-x-reverse));margin-left:calc(0.5rem * calc(1 - var(--tw-space-x-reverse)))}.space-x-3 > :not([hidden]) ~ :not([hidden]){--tw-space-x-reverse:0;margin-right:calc(0.75rem * var(--tw-space-x-reverse));margin-left:calc(0.75rem * calc(1 - var(--tw-space-x-reverse)))}.space-y-1 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(0.25rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(0.25rem * var(--tw-space-y-reverse))}.space-y-2 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(0.5rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(0.5rem * var(--tw-space-y-reverse))}.space-y-3 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(0.75rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(0.75rem * var(--tw-space-y-reverse))}.space-y-5 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(1.25rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(1.25rem * var(--tw-space-y-reverse))}.space-y-6 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(1.5rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(1.5rem * var(--tw-space-y-reverse))}.space-y-8 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(2rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(2rem * var(--tw-space-y-reverse))}.divide-y > :not([hidden]) ~ :not([hidden]){--tw-divide-y-reverse:0;border-top-width:calc(1px * calc(1 - var(--tw-divide-y-reverse)));border-bottom-width:calc(1px * var(--tw-divide-y-reverse))}.divide-slate-100 > :not([hidden]) ~ :not([hidden]){--tw-divide-opacity:1;border-color:rgb(241 245 249 / var(--tw-divide-opacity, 1))}.self-start{align-self:flex-start}.overflow-hidden{overflow:hidden}.overflow-x-auto{overflow-x:auto}.truncate{overflow:hidden;text-overflow:ellipsis;white-space:nowrap}.whitespace-nowrap{white-space:nowrap}.rounded-2xl{border-radius:1rem}.rounded-full{border-radius:9999px}.rounded-lg{border-radius:0.5rem}.rounded-xl{border-radius:0.75rem}.border{border-width:1px}.border-b{border-bottom-width:1px}.border-t{border-top-width:1px}.border-amber-200{--tw-border-opacity:1;border-color:rgb(253 230 138 / var(--tw-border-opacity, 1))}.border-emerald-200{--tw-border-opacity:1;border-color:rgb(167 243 208 / var(--tw-border-opacity, 1))}.border-indigo-100{--tw-border-opacity:1;border-color:rgb(224 231 255 / var(--tw-border-opacity, 1))}.border-indigo-200{--tw-border-opacity:1;border-color:rgb(199 210 254 / var(--tw-border-opacity, 1))}.border-slate-100{--tw-border-opacity:1;border-color:rgb(241 245 249 / var(--tw-border-opacity, 1))}.border-slate-200{--tw-border-opacity:1;border-color:rgb(226 232 240 / var(--tw-border-opacity, 1))}.border-slate-200\/80{border-color:rgb(226 232 240 / 0.8)}.border-slate-300{--tw-border-opacity:1;border-color:rgb(203 213 225 / var(--tw-border-opacity, 1))}.border-slate-800{--tw-border-opacity:1;border-color:rgb(30 41 59 / var(--tw-border-opacity, 1))}.border-slate-200\/90{border-color:rgb(226 232 240 / 0.9)}.bg-slate-50{--tw-bg-opacity:1;background-color:rgb(248 250 252 / var(--tw-bg-opacity, 1))}.bg-amber-50{--tw-bg-opacity:1;background-color:rgb(255 251 235 / var(--tw-bg-opacity, 1))}.bg-emerald-100{--tw-bg-opacity:1;background-color:rgb(209 250 229 / var(--tw-bg-opacity, 1))}.bg-emerald-50{--tw-bg-opacity:1;background-color:rgb(236 253 245 / var(--tw-bg-opacity, 1))}.bg-emerald-500{--tw-bg-opacity:1;background-color:rgb(16 185 129 / var(--tw-bg-opacity, 1))}.bg-emerald-600{--tw-bg-opacity:1;background-color:rgb(5 150 105 / var(--tw-bg-opacity, 1))}.bg-indigo-100{--tw-bg-opacity:1;background-color:rgb(224 231 255 / var(--tw-bg-opacity, 1))}.bg-indigo-50{--tw-bg-opacity:1;background-color:rgb(238 242 255 / var(--tw-bg-opacity, 1))}.bg-indigo-600{--tw-bg-opacity:1;background-color:rgb(79 70 229 / var(--tw-bg-opacity, 1))}.bg-indigo-700{--tw-bg-opacity:1;background-color:rgb(67 56 202 / var(--tw-bg-opacity, 1))}.bg-indigo-900{--tw-bg-opacity:1;background-color:rgb(49 46 129 / var(--tw-bg-opacity, 1))}.bg-red-50{--tw-bg-opacity:1;background-color:rgb(254 242 242 / var(--tw-bg-opacity, 1))}.bg-slate-100{--tw-bg-opacity:1;background-color:rgb(241 245 249 / var(--tw-bg-opacity, 1))}.bg-slate-900{--tw-bg-opacity:1;background-color:rgb(15 23 42 / var(--tw-bg-opacity, 1))}.bg-slate-900\/60{background-color:rgb(15 23 42 / 0.6)}.bg-white{--tw-bg-opacity:1;background-color:rgb(255 255 255 / var(--tw-bg-opacity, 1))}.bg-amber-100{--tw-bg-opacity:1;background-color:rgb(254 243 199 / var(--tw-bg-opacity, 1))}.bg-blue-100{--tw-bg-opacity:1;background-color:rgb(219 234 254 / var(--tw-bg-opacity, 1))}.bg-indigo-50\/60{background-color:rgb(238 242 255 / 0.6)}.bg-purple-100{--tw-bg-opacity:1;background-color:rgb(243 232 255 / var(--tw-bg-opacity, 1))}.bg-slate-50\/50{background-color:rgb(248 250 252 / 0.5)}.object-contain{object-fit:contain}.p-1{padding:0.25rem}.p-2{padding:0.5rem}.p-2\.5{padding:0.625rem}.p-3{padding:0.75rem}.p-4{padding:1rem}.p-5{padding:1.25rem}.p-6{padding:1.5rem}.px-2\.5{padding-left:0.625rem;padding-right:0.625rem}.px-3{padding-left:0.75rem;padding-right:0.75rem}.px-4{padding-left:1rem;padding-right:1rem}.px-5{padding-left:1.25rem;padding-right:1.25rem}.px-8{padding-left:2rem;padding-right:2rem}.py-0\.5{padding-top:0.125rem;padding-bottom:0.125rem}.py-1{padding-top:0.25rem;padding-bottom:0.25rem}.py-1\.5{padding-top:0.375rem;padding-bottom:0.375rem}.py-2{padding-top:0.5rem;padding-bottom:0.5rem}.py-2\.5{padding-top:0.625rem;padding-bottom:0.625rem}.py-3{padding-top:0.75rem;padding-bottom:0.75rem}.py-6{padding-top:1.5rem;padding-bottom:1.5rem}.px-2{padding-left:0.5rem;padding-right:0.5rem}.pb-3{padding-bottom:0.75rem}.pb-4{padding-bottom:1rem}.pt-2{padding-top:0.5rem}.pt-6{padding-top:1.5rem}.pt-1{padding-top:0.25rem}.text-left{text-align:left}.text-center{text-align:center}.font-sans{font-family:Inter, sans-serif}.font-mono{font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace}.text-2xl{font-size:1.5rem;line-height:2rem}.text-\[11px\]{font-size:11px}.text-lg{font-size:1.125rem;line-height:1.75rem}.text-sm{font-size:0.875rem;line-height:1.25rem}.text-xl{font-size:1.25rem;line-height:1.75rem}.text-xs{font-size:0.75rem;line-height:1rem}.text-\[10px\]{font-size:10px}.text-base{font-size:1rem;line-height:1.5rem}.font-bold{font-weight:700}.font-extrabold{font-weight:800}.font-medium{font-weight:500}.font-semibold{font-weight:600}.uppercase{text-transform:uppercase}.leading-tight{line-height:1.25}.tracking-wider{letter-spacing:0.05em}.text-slate-800{--tw-text-opacity:1;color:rgb(30 41 59 / var(--tw-text-opacity, 1))}.text-amber-600{--tw-text-opacity:1;color:rgb(217 119 6 / var(--tw-text-opacity, 1))}.text-amber-900{--tw-text-opacity:1;color:rgb(120 53 15 / var(--tw-text-opacity, 1))}.text-emerald-600{--tw-text-opacity:1;color:rgb(5 150 105 / var(--tw-text-opacity, 1))}.text-emerald-800{--tw-text-opacity:1;color:rgb(6 95 70 / var(--tw-text-opacity, 1))}.text-indigo-200{--tw-text-opacity:1;color:rgb(199 210 254 / var(--tw-text-opacity, 1))}.text-indigo-300{--tw-text-opacity:1;color:rgb(165 180 252 / var(--tw-text-opacity, 1))}.text-indigo-600{--tw-text-opacity:1;color:rgb(79 70 229 / var(--tw-text-opacity, 1))}.text-indigo-700{--tw-text-opacity:1;color:rgb(67 56 202 / var(--tw-text-opacity, 1))}.text-indigo-800{--tw-text-opacity:1;color:rgb(55 48 163 / var(--tw-text-opacity, 1))}.text-indigo-900{--tw-text-opacity:1;color:rgb(49 46 129 / var(--tw-text-opacity, 1))}.text-red-600{--tw-text-opacity:1;color:rgb(220 38 38 / var(--tw-text-opacity, 1))}.text-slate-300{--tw-text-opacity:1;color:rgb(203 213 225 / var(--tw-text-opacity, 1))}.text-slate-400{--tw-text-opacity:1;color:rgb(148 163 184 / var(--tw-text-opacity, 1))}.text-slate-500{--tw-text-opacity:1;color:rgb(100 116 139 / var(--tw-text-opacity, 1))}.text-slate-600{--tw-text-opacity:1;color:rgb(71 85 105 / var(--tw-text-opacity, 1))}.text-slate-700{--tw-text-opacity:1;color:rgb(51 65 85 / var(--tw-text-opacity, 1))}.text-slate-900{--tw-text-opacity:1;color:rgb(15 23 42 / var(--tw-text-opacity, 1))}.text-white{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.text-amber-800{--tw-text-opacity:1;color:rgb(146 64 14 / var(--tw-text-opacity, 1))}.text-blue-800{--tw-text-opacity:1;color:rgb(30 64 175 / var(--tw-text-opacity, 1))}.text-purple-600{--tw-text-opacity:1;color:rgb(147 51 234 / var(--tw-text-opacity, 1))}.text-purple-800{--tw-text-opacity:1;color:rgb(107 33 168 / var(--tw-text-opacity, 1))}.text-blue-400{--tw-text-opacity:1;color:rgb(96 165 250 / var(--tw-text-opacity, 1))}.text-emerald-400{--tw-text-opacity:1;color:rgb(52 211 153 / var(--tw-text-opacity, 1))}.antialiased{-webkit-font-smoothing:antialiased;-moz-osx-font-smoothing:grayscale}.opacity-0{opacity:0}.shadow{--tw-shadow:0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 1px 3px 0 var(--tw-shadow-color), 0 1px 2px -1px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-2xl{--tw-shadow:0 25px 50px -12px rgb(0 0 0 / 0.25);--tw-shadow-colored:0 25px 50px -12px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-lg{--tw-shadow:0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 10px 15px -3px var(--tw-shadow-color), 0 4px 6px -4px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-sm{--tw-shadow:0 1px 2px 0 rgb(0 0 0 / 0.05);--tw-shadow-colored:0 1px 2px 0 var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-xl{--tw-shadow:0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 20px 25px -5px var(--tw-shadow-color), 0 8px 10px -6px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-indigo-200{--tw-shadow-color:#c7d2fe;--tw-shadow:var(--tw-shadow-colored)}.backdrop-blur-sm{--tw-backdrop-blur:blur(4px);-webkit-backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia)}.transition{transition-property:color, background-color, border-color, fill, stroke, opacity, box-shadow, transform, filter, -webkit-text-decoration-color, -webkit-backdrop-filter;transition-property:color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, backdrop-filter;transition-property:color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, backdrop-filter, -webkit-text-decoration-color, -webkit-backdrop-filter;transition-timing-function:cubic-bezier(0.4, 0, 0.2, 1);transition-duration:150ms}.transition-all{transition-property:all;transition-timing-function:cubic-bezier(0.4, 0, 0.2, 1);transition-duration:150ms}.duration-300{transition-duration:300ms}.selection\:bg-indigo-500 *::selection{--tw-bg-opacity:1;background-color:rgb(99 102 241 / var(--tw-bg-opacity, 1))}.selection\:text-white *::selection{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.selection\:bg-indigo-500::selection{--tw-bg-opacity:1;background-color:rgb(99 102 241 / var(--tw-bg-opacity, 1))}.selection\:text-white::selection{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.hover\:border-indigo-400:hover{--tw-border-opacity:1;border-color:rgb(129 140 248 / var(--tw-border-opacity, 1))}.hover\:border-indigo-500:hover{--tw-border-opacity:1;border-color:rgb(99 102 241 / var(--tw-border-opacity, 1))}.hover\:bg-emerald-700:hover{--tw-bg-opacity:1;background-color:rgb(4 120 87 / var(--tw-bg-opacity, 1))}.hover\:bg-indigo-700:hover{--tw-bg-opacity:1;background-color:rgb(67 56 202 / var(--tw-bg-opacity, 1))}.hover\:bg-indigo-800:hover{--tw-bg-opacity:1;background-color:rgb(55 48 163 / var(--tw-bg-opacity, 1))}.hover\:bg-red-100:hover{--tw-bg-opacity:1;background-color:rgb(254 226 226 / var(--tw-bg-opacity, 1))}.hover\:bg-slate-200:hover{--tw-bg-opacity:1;background-color:rgb(226 232 240 / var(--tw-bg-opacity, 1))}.hover\:bg-white:hover{--tw-bg-opacity:1;background-color:rgb(255 255 255 / var(--tw-bg-opacity, 1))}.hover\:bg-indigo-50\/30:hover{background-color:rgb(238 242 255 / 0.3)}.hover\:bg-slate-50\/80:hover{background-color:rgb(248 250 252 / 0.8)}.hover\:text-slate-600:hover{--tw-text-opacity:1;color:rgb(71 85 105 / var(--tw-text-opacity, 1))}.hover\:text-white:hover{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.hover\:shadow-sm:hover{--tw-shadow:0 1px 2px 0 rgb(0 0 0 / 0.05);--tw-shadow-colored:0 1px 2px 0 var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.hover\:shadow-md:hover{--tw-shadow:0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 4px 6px -1px var(--tw-shadow-color), 0 2px 4px -2px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.hover\:shadow-indigo-300:hover{--tw-shadow-color:#a5b4fc;--tw-shadow:var(--tw-shadow-colored)}.focus\:outline-none:focus{outline:2px solid transparent;outline-offset:2px}.focus\:ring-2:focus{--tw-ring-offset-shadow:var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);--tw-ring-shadow:var(--tw-ring-inset) 0 0 0 calc(2px + var(--tw-ring-offset-width)) var(--tw-ring-color);box-shadow:var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000)}.focus\:ring-indigo-500:focus{--tw-ring-opacity:1;--tw-ring-color:rgb(99 102 241 / var(--tw-ring-opacity, 1))}@media (min-width: 640px){.sm\:inline{display:inline}.sm\:grid-cols-2{grid-template-columns:repeat(2, minmax(0, 1fr))}.sm\:grid-cols-3{grid-template-columns:repeat(3, minmax(0, 1fr))}.sm\:flex-row{flex-direction:row}.sm\:items-center{align-items:center}.sm\:space-x-2 > :not([hidden]) ~ :not([hidden]){--tw-space-x-reverse:0;margin-right:calc(0.5rem * var(--tw-space-x-reverse));margin-left:calc(0.5rem * calc(1 - var(--tw-space-x-reverse)))}.sm\:p-8{padding:2rem}.sm\:px-6{padding-left:1.5rem;padding-right:1.5rem}}@media (min-width: 768px){.md\:grid-cols-3{grid-template-columns:repeat(3, minmax(0, 1fr))}}@media (min-width: 1024px){.lg\:col-span-6{grid-column:span 6 / span 6}.lg\:w-auto{width:auto}.lg\:flex-none{flex:none}.lg\:grid-cols-12{grid-template-columns:repeat(12, minmax(0, 1fr))}.lg\:grid-cols-6{grid-template-columns:repeat(6, minmax(0, 1fr))}.lg\:flex-row{flex-direction:row}.lg\:items-center{align-items:center}.lg\:px-8{padding-left:2rem;padding-right:2rem}}</style></head>
<body class="h-full flex flex-col font-sans text-slate-800 antialiased selection:bg-indigo-500 selection:text-white">

    <!-- Header Navigation Bar -->
    <header class="bg-indigo-900 text-white shadow-lg sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <!-- Logo / Title -->
                <div class="flex items-center space-x-3">
                    <div class="p-2 bg-indigo-600 rounded-xl shadow">
                        <i class="fa-solid fa-chart-pie text-xl text-white"></i>
                    </div>
                    <div>
                        <h1 class="font-bold text-lg leading-tight">StatTeen 15-17</h1>
                        <p class="text-xs text-indigo-300">Pesquisa &amp; Análise Estatística em Tempo Real</p>
                    </div>
                </div>

                <!-- Navigation Tabs -->
                <nav class="flex space-x-1 sm:space-x-2">
                    <button id="tab-btn-dashboard" onclick="switchTab('dashboard')" class="px-3 py-2 text-sm font-medium rounded-lg transition-all flex items-center space-x-2 bg-indigo-700 text-white shadow">
                        <i class="fa-solid fa-chart-column"></i>
                        <span class="hidden sm:inline">Resultados &amp; Gráficos</span>
                    </button>
                    <button id="tab-btn-survey" onclick="switchTab('survey')" class="px-3 py-2 text-sm font-medium rounded-lg transition-all flex items-center space-x-2 text-indigo-200 hover:text-white hover:bg-indigo-800">
                        <i class="fa-solid fa-clipboard-question"></i>
                        <span class="hidden sm:inline">Responder Pesquisa</span>
                    </button>
                    <button id="tab-btn-responses" onclick="switchTab('responses')" class="px-3 py-2 text-sm font-medium rounded-lg transition-all flex items-center space-x-2 text-indigo-200 hover:text-white hover:bg-indigo-800">
                        <i class="fa-solid fa-table"></i>
                        <span class="hidden sm:inline">Dados Brutos</span>
                    </button>
                    <button id="tab-btn-hosting" onclick="switchTab('hosting')" class="px-3 py-2 text-sm font-medium rounded-lg transition-all flex items-center space-x-2 text-indigo-200 hover:text-white hover:bg-indigo-800">
                        <i class="fa-solid fa-globe"></i>
                        <span class="hidden sm:inline">Como Hospedar</span>
                    </button>
                </nav>
            </div>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="flex-1 max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6">

        <!-- Notification Toast Toast Container -->
        <div id="toast-container" class="fixed bottom-5 right-5 z-50 flex flex-col space-y-2"></div>

        <!-- SHARE & QUICK ACTIONS MODAL -->
        <div id="share-modal" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 flex items-center justify-center p-4">
            <div class="bg-white rounded-2xl shadow-2xl max-w-lg w-full p-6 space-y-5 transform transition-all">
                <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                    <h3 class="font-bold text-lg text-slate-800 flex items-center gap-2">
                        <i class="fa-solid fa-share-nodes text-indigo-600"></i> Compartilhar Pesquisa Online
                    </h3>
                    <button onclick="toggleShareModal()" class="text-slate-400 hover:text-slate-600 p-1">
                        <i class="fa-solid fa-xmark text-lg"></i>
                    </button>
                </div>
                
                <!-- Cloud Status Indicator -->
                <div id="cloud-status-badge" class="flex items-center gap-2 p-2.5 bg-emerald-50 text-emerald-800 rounded-xl text-xs font-semibold border border-emerald-200">
                    <span class="w-2.5 h-2.5 rounded-full bg-emerald-500 animate-pulse"></span>
                    <span>Sincronização em Nuvem Ativa (Respostas compartilhadas em tempo real)</span>
                </div>

                <!-- QR Code & Share Link Section -->
                <div class="flex flex-col sm:flex-row items-center gap-4 bg-slate-50 p-4 rounded-xl border border-slate-200">
                    <div id="qr-code-container" class="bg-white p-2 rounded-lg border border-slate-200 flex-shrink-0"><img src="https://api.qrserver.com/v1/create-qr-code/?size=120x120&amp;data=blob%3Ahttps%3A%2F%2F45p8jr29hjn2p9akq5kkkqda4qb36r7fjpqrv4cxjvchhkb9cy-h1013078785.scf.usercontent.goog%2F174f9267-608b-4073-9189-1425e9572054" alt="QR Code Pesquisa" class="w-28 h-28 object-contain"></div>
                    <div class="space-y-2 w-full">
                        <label class="block text-xs font-bold text-slate-600 uppercase">Link da Pesquisa</label>
                        <p class="text-[11px] text-slate-500">Escaneie o QR Code com o celular ou copie o link abaixo para enviar aos participantes:</p>
                        <div class="flex gap-2">
                            <input id="share-link-input" type="text" readonly="" class="flex-1 bg-white border border-slate-300 rounded-lg px-3 py-2 text-xs font-mono text-slate-700 focus:outline-none" value="">
                            <button onclick="copyShareLink()" class="bg-indigo-600 hover:bg-indigo-700 text-white px-3 py-2 rounded-lg text-xs font-semibold flex items-center gap-1 shadow transition">
                                <i class="fa-solid fa-copy"></i> Copiar
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Direct Download Option -->
                <div class="p-3 bg-indigo-50 border border-indigo-100 rounded-xl flex items-center justify-between">
                    <div>
                        <h4 class="text-xs font-bold text-indigo-900">Quer publicar em seu próprio site?</h4>
                        <p class="text-[11px] text-indigo-700">Baixe o arquivo HTML completo e publique no GitHub Pages ou Netlify.</p>
                    </div>
                    <button onclick="downloadHTMLFile()" class="px-3 py-1.5 bg-indigo-600 hover:bg-indigo-700 text-white text-xs font-semibold rounded-lg shadow transition flex items-center gap-1">
                        <i class="fa-solid fa-download"></i> Baixar HTML
                    </button>
                </div>

                <div class="pt-2 border-t border-slate-100 flex justify-end">
                    <button onclick="toggleShareModal()" class="px-4 py-2 bg-slate-100 text-slate-700 hover:bg-slate-200 text-xs font-semibold rounded-lg transition">
                        Fechar
                    </button>
                </div>
            </div>
        </div>

        <!-- SECTION 1: DASHBOARD DE RESULTADOS (DEFAULT TAB) -->
        <section id="tab-dashboard" class="space-y-6">
            
            <!-- Global Overview & Controls Header -->
            <div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/80 flex flex-col lg:flex-row items-start lg:items-center justify-between gap-6">
                <div>
                    <div class="flex items-center gap-2">
                        <span class="px-2.5 py-0.5 rounded-full text-xs font-semibold bg-indigo-100 text-indigo-800">Universo: Adolescentes (15 a 17 anos)</span>
                        <span id="response-count-badge" class="px-2.5 py-0.5 rounded-full text-xs font-semibold bg-emerald-100 text-emerald-800">Total: 0 Respostas</span>
                    </div>
                    <h2 class="text-2xl font-extrabold text-slate-900 mt-2">Painel de Estatísticas &amp; Gráficos</h2>
                    <p class="text-sm text-slate-500">Resultados consolidados em tempo real com tabelas de frequência absoluta/relativa e medidas descritivas.</p>
                </div>

                <!-- Action Controls -->
                <div class="flex flex-wrap gap-2 w-full lg:w-auto">
                    <button onclick="toggleShareModal()" class="flex-1 lg:flex-none px-4 py-2 bg-indigo-600 hover:bg-indigo-700 text-white rounded-xl text-xs font-semibold flex items-center justify-center gap-2 shadow-sm transition">
                        <i class="fa-solid fa-link"></i> Link p/ Compartilhar
                    </button>
                    <button onclick="generateMockResponses(5)" class="flex-1 lg:flex-none px-4 py-2 bg-emerald-600 hover:bg-emerald-700 text-white rounded-xl text-xs font-semibold flex items-center justify-center gap-2 shadow-sm transition" title="Adiciona 5 respostas de adolescentes fictícios para demonstrar recálculo em tempo real">
                        <i class="fa-solid fa-user-plus"></i> +5 Respostas Demo
                    </button>
                    <button onclick="exportDataJSON()" class="px-3 py-2 bg-slate-100 hover:bg-slate-200 text-slate-700 rounded-xl text-xs font-semibold flex items-center gap-1 transition" title="Exportar Dados em JSON">
                        <i class="fa-solid fa-download"></i>
                    </button>
                    <button onclick="resetDataConfirmation()" class="px-3 py-2 bg-red-50 hover:bg-red-100 text-red-600 rounded-xl text-xs font-semibold flex items-center gap-1 transition" title="Reiniciar Dados">
                        <i class="fa-solid fa-trash-can"></i>
                    </button>
                </div>
            </div>

            <!-- Variable Types Breakdown Legend / Filter -->
            <div class="bg-slate-100 rounded-xl p-3 flex flex-wrap items-center justify-between gap-3 text-xs">
                <span class="font-semibold text-slate-600">Filtrar por Tipo de Variável:</span>
                <div class="flex flex-wrap gap-2">
                    <button onclick="filterDashboard('ALL')" id="filter-btn-ALL" class="px-3 py-1.5 rounded-lg font-semibold bg-white text-indigo-700 shadow-sm border border-indigo-200">Todas (20)</button>
                    <button onclick="filterDashboard('NOMINAL')" id="filter-btn-NOMINAL" class="px-3 py-1.5 rounded-lg font-semibold text-slate-600 hover:bg-white hover:shadow-sm">Qualitativa Nominal (5)</button>
                    <button onclick="filterDashboard('ORDINAL')" id="filter-btn-ORDINAL" class="px-3 py-1.5 rounded-lg font-semibold text-slate-600 hover:bg-white hover:shadow-sm">Qualitativa Ordinal (5)</button>
                    <button onclick="filterDashboard('DISCRETA')" id="filter-btn-DISCRETA" class="px-3 py-1.5 rounded-lg font-semibold text-slate-600 hover:bg-white hover:shadow-sm">Quantitativa Discreta (5)</button>
                    <button onclick="filterDashboard('CONTINUA')" id="filter-btn-CONTINUA" class="px-3 py-1.5 rounded-lg font-semibold text-slate-600 hover:bg-white hover:shadow-sm">Quantitativa Contínua (5)</button>
                </div>
            </div>

            <!-- Dynamic Dashboard Cards Container -->
            <div id="questions-dashboard-container" class="space-y-8"><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #1</span>
                                <span class="bg-blue-100 text-blue-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Nominal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Rede social mais utilizada no dia a dia</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Setores (Pizza)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q1" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #2</span>
                                <span class="bg-blue-100 text-blue-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Nominal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Estilo musical preferido</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Setores (Pizza)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q2" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #3</span>
                                <span class="bg-blue-100 text-blue-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Nominal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Principal dispositivo utilizado para estudos e tarefas</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Setores (Pizza)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q3" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #4</span>
                                <span class="bg-blue-100 text-blue-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Nominal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Principal meio de acesso a notícias e atualidades</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Setores (Pizza)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q4" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #5</span>
                                <span class="bg-blue-100 text-blue-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Nominal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Área do conhecimento que pretende seguir no futuro</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Setores (Pizza)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q5" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #6</span>
                                <span class="bg-purple-100 text-purple-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Ordinal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Nível habitual de estresse em relação aos estudos escolares</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Linhas (Tendência)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q6" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #7</span>
                                <span class="bg-purple-100 text-purple-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Ordinal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Frequência de preocupação com o futuro profissional e vestibulares</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Linhas (Tendência)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q7" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #8</span>
                                <span class="bg-purple-100 text-purple-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Ordinal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Autoavaliação do desempenho escolar atual</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Linhas (Tendência)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q8" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #9</span>
                                <span class="bg-purple-100 text-purple-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Ordinal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Grau de concordância: "A Inteligência Artificial trará impactos positivos para os jovens"</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Linhas (Tendência)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q9" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #10</span>
                                <span class="bg-purple-100 text-purple-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Ordinal</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Frequência de prática de hábitos de saúde (hidratação, alimentação equilibrada)</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null </span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Linhas (Tendência)
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q10" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #11</span>
                                <span class="bg-amber-100 text-amber-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Discreta</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Quantidade de redes sociais diferentes acessadas diariamente</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null redes</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Barras Discretas
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q11" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #12</span>
                                <span class="bg-amber-100 text-amber-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Discreta</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Quantidade de livros lidos por ano (fora os de leitura obrigatória)</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null livros</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Barras Discretas
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q12" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #13</span>
                                <span class="bg-amber-100 text-amber-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Discreta</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Quantos dias por semana pratica esportes ou atividade física</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null dias</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Barras Discretas
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q13" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #14</span>
                                <span class="bg-amber-100 text-amber-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Discreta</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Número de amigos próximos (de real confiança)</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null amigos</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Barras Discretas
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q14" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #15</span>
                                <span class="bg-amber-100 text-amber-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Discreta</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Horas médias de sono por noite nos dias de aula</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null horas</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Gráfico de Barras Discretas
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q15" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #16</span>
                                <span class="bg-emerald-100 text-emerald-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Contínua</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Tempo médio diário de uso de tela no smartphone (horas)</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null h</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Histograma de Frequências
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q16" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #17</span>
                                <span class="bg-emerald-100 text-emerald-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Contínua</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Estimativa de gastos pessoais semanais com lazer/lanches (em R$)</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null R$</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Histograma de Frequências
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q17" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #18</span>
                                <span class="bg-emerald-100 text-emerald-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Contínua</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Altura aproximada (em metros)</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null m</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Histograma de Frequências
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q18" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #19</span>
                                <span class="bg-emerald-100 text-emerald-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Contínua</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Horas semanais dedicadas a hobbies fora das telas (esporte, música, desenho, etc.)</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null h</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Histograma de Frequências
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q19" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div><div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #20</span>
                                <span class="bg-emerald-100 text-emerald-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Contínua</span>
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">Tempo de deslocamento diário até a escola (em minutos)</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">0</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($ar{x}$)</span>
                            <span class="text-base font-extrabold text-indigo-600">null min</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="null">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold text-purple-600">null</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold text-emerald-600">null</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($sum$)</td>
                                        <td class="p-2.5 text-center">0</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: Histograma de Frequências
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-q20" width="801" height="256" style="display: block; box-sizing: border-box; height: 256px; width: 801px;"></canvas>
                            </div>
                        </div>
                    </div>
                </div></div>

        </section>

        <!-- SECTION 2: FORMULÁRIO DA PESQUISA ONLINE -->
        <section id="tab-survey" class="hidden space-y-6 max-w-4xl mx-auto">
            <div class="bg-white rounded-2xl p-6 sm:p-8 shadow-sm border border-slate-200">
                <div class="border-b border-slate-200 pb-4 mb-6">
                    <span class="text-xs font-bold uppercase tracking-wider text-indigo-600 bg-indigo-50 px-3 py-1 rounded-full">Questionário Jovem</span>
                    <h2 class="text-2xl font-bold text-slate-900 mt-2">Pesquisa de Opinião e Hábitos (15 a 17 Anos)</h2>
                    <p class="text-sm text-slate-500 mt-1">
                        Responda com sinceridade às 20 perguntas abaixo. Todas as respostas são anônimas e serão agregadas para a análise estatística.
                    </p>
                </div>

                <form id="survey-form" onsubmit="handleFormSubmit(event)" class="space-y-8">
                    <!-- Form Questions Container (Generated via JS for 20 questions) -->
                    <div id="survey-questions-list" class="space-y-8">
                <div class="p-5 bg-indigo-50/60 border border-indigo-100 rounded-2xl">
                    <label class="block font-bold text-slate-800 text-sm mb-2">Qual é a sua idade atual?</label>
                    <div class="flex gap-4">
                        
                            <label class="flex items-center gap-2 bg-white px-4 py-2 border border-slate-300 rounded-xl cursor-pointer hover:border-indigo-500 font-semibold text-xs">
                                <input type="radio" name="age" value="15" required="">
                                <span>15 anos</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-white px-4 py-2 border border-slate-300 rounded-xl cursor-pointer hover:border-indigo-500 font-semibold text-xs">
                                <input type="radio" name="age" value="16" required="" checked="">
                                <span>16 anos</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-white px-4 py-2 border border-slate-300 rounded-xl cursor-pointer hover:border-indigo-500 font-semibold text-xs">
                                <input type="radio" name="age" value="17" required="">
                                <span>17 anos</span>
                            </label>
                        
                    </div>
                </div>
            
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 1 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-blue-100 text-blue-800">Qualitativa Nominal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Rede social mais utilizada no dia a dia</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q1" value="Instagram" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Instagram</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q1" value="TikTok" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">TikTok</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q1" value="YouTube" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">YouTube</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q1" value="WhatsApp" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">WhatsApp</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q1" value="Discord" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Discord</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q1" value="X (Twitter)" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">X (Twitter)</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 2 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-blue-100 text-blue-800">Qualitativa Nominal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Estilo musical preferido</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q2" value="Funk" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Funk</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q2" value="Pop" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Pop</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q2" value="Trap / Rap" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Trap / Rap</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q2" value="Sertanejo" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Sertanejo</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q2" value="Rock / Indie" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Rock / Indie</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q2" value="K-Pop" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">K-Pop</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q2" value="Eletrônica" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Eletrônica</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 3 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-blue-100 text-blue-800">Qualitativa Nominal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Principal dispositivo utilizado para estudos e tarefas</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q3" value="Smartphone" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Smartphone</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q3" value="Notebook / PC" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Notebook / PC</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q3" value="Tablet" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Tablet</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 4 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-blue-100 text-blue-800">Qualitativa Nominal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Principal meio de acesso a notícias e atualidades</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q4" value="Redes Sociais" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Redes Sociais</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q4" value="Portais de Notícias" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Portais de Notícias</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q4" value="YouTube / Podcasts" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">YouTube / Podcasts</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q4" value="Televisão" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Televisão</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q4" value="Conversas Família/Amigos" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Conversas Família/Amigos</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 5 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-blue-100 text-blue-800">Qualitativa Nominal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Área do conhecimento que pretende seguir no futuro</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q5" value="Exatas e Tecnologia" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Exatas e Tecnologia</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q5" value="Biológicas e Saúde" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Biológicas e Saúde</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q5" value="Humanas e Sociais" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Humanas e Sociais</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q5" value="Artes e Comunicação" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Artes e Comunicação</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q5" value="Ainda Não Sei" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Ainda Não Sei</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 6 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-purple-100 text-purple-800">Qualitativa Ordinal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Nível habitual de estresse em relação aos estudos escolares</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q6" value="1 - Muito Baixo" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">1 - Muito Baixo</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q6" value="2 - Baixo" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">2 - Baixo</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q6" value="3 - Moderado" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">3 - Moderado</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q6" value="4 - Alto" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">4 - Alto</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q6" value="5 - Muito Alto" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">5 - Muito Alto</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 7 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-purple-100 text-purple-800">Qualitativa Ordinal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Frequência de preocupação com o futuro profissional e vestibulares</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q7" value="Nunca" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Nunca</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q7" value="Raramente" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Raramente</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q7" value="Às Vezes" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Às Vezes</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q7" value="Frequentemente" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Frequentemente</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q7" value="Sempre" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Sempre</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 8 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-purple-100 text-purple-800">Qualitativa Ordinal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Autoavaliação do desempenho escolar atual</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q8" value="Insuficiente" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Insuficiente</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q8" value="Regular" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Regular</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q8" value="Bom" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Bom</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q8" value="Muito Bom" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Muito Bom</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q8" value="Excelente" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Excelente</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 9 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-purple-100 text-purple-800">Qualitativa Ordinal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Grau de concordância: "A Inteligência Artificial trará impactos positivos para os jovens"</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q9" value="Discordo Totalmente" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Discordo Totalmente</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q9" value="Discordo Parcialmente" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Discordo Parcialmente</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q9" value="Neutro" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Neutro</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q9" value="Concordo Parcialmente" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Concordo Parcialmente</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q9" value="Concordo Totalmente" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Concordo Totalmente</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 10 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-purple-100 text-purple-800">Qualitativa Ordinal</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Frequência de prática de hábitos de saúde (hidratação, alimentação equilibrada)</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q10" value="Raramente" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Raramente</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q10" value="Às Vezes" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Às Vezes</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q10" value="Frequência Moderada" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Frequência Moderada</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q10" value="Quase Sempre" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Quase Sempre</span>
                            </label>
                        
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="q10" value="Sempre" required="" class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">Sempre</span>
                            </label>
                        </div></div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 11 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-amber-100 text-amber-800">Quantitativa Discreta</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Quantidade de redes sociais diferentes acessadas diariamente</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q11" min="1" max="8" step="1" required="" class="w-32 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 4">
                            <span class="text-xs font-medium text-slate-500">redes</span>
                        </div>
                    </div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 12 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-amber-100 text-amber-800">Quantitativa Discreta</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Quantidade de livros lidos por ano (fora os de leitura obrigatória)</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q12" min="0" max="15" step="1" required="" class="w-32 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 7">
                            <span class="text-xs font-medium text-slate-500">livros</span>
                        </div>
                    </div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 13 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-amber-100 text-amber-800">Quantitativa Discreta</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Quantos dias por semana pratica esportes ou atividade física</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q13" min="0" max="7" step="1" required="" class="w-32 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 3">
                            <span class="text-xs font-medium text-slate-500">dias</span>
                        </div>
                    </div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 14 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-amber-100 text-amber-800">Quantitativa Discreta</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Número de amigos próximos (de real confiança)</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q14" min="0" max="10" step="1" required="" class="w-32 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 5">
                            <span class="text-xs font-medium text-slate-500">amigos</span>
                        </div>
                    </div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 15 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-amber-100 text-amber-800">Quantitativa Discreta</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Horas médias de sono por noite nos dias de aula</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q15" min="4" max="10" step="1" required="" class="w-32 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 7">
                            <span class="text-xs font-medium text-slate-500">horas</span>
                        </div>
                    </div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 16 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-emerald-100 text-emerald-800">Quantitativa Contínua</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Tempo médio diário de uso de tela no smartphone (horas)</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q16" min="1" max="14" step="0.5" required="" class="w-36 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 7.5">
                            <span class="text-xs font-medium text-slate-500">h</span>
                        </div>
                    </div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 17 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-emerald-100 text-emerald-800">Quantitativa Contínua</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Estimativa de gastos pessoais semanais com lazer/lanches (em R$)</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q17" min="0" max="200" step="5" required="" class="w-36 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 100.0">
                            <span class="text-xs font-medium text-slate-500">R$</span>
                        </div>
                    </div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 18 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-emerald-100 text-emerald-800">Quantitativa Contínua</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Altura aproximada (em metros)</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q18" min="1.45" max="2.05" step="0.01" required="" class="w-36 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 1.8">
                            <span class="text-xs font-medium text-slate-500">m</span>
                        </div>
                    </div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 19 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-emerald-100 text-emerald-800">Quantitativa Contínua</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Horas semanais dedicadas a hobbies fora das telas (esporte, música, desenho, etc.)</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q19" min="0" max="25" step="0.5" required="" class="w-36 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 12.5">
                            <span class="text-xs font-medium text-slate-500">h</span>
                        </div>
                    </div>
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta 20 de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full bg-emerald-100 text-emerald-800">Quantitativa Contínua</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Tempo de deslocamento diário até a escola (em minutos)</h3>
                
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="q20" min="5" max="90" step="5" required="" class="w-36 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none" placeholder="Ex: 47.5">
                            <span class="text-xs font-medium text-slate-500">min</span>
                        </div>
                    </div></div>

                    <!-- Submit Button -->
                    <div class="pt-6 border-t border-slate-200 flex items-center justify-between">
                        <button type="button" onclick="switchTab('dashboard')" class="px-5 py-2.5 bg-slate-100 hover:bg-slate-200 text-slate-700 text-sm font-semibold rounded-xl transition">
                            Cancelar
                        </button>
                        <button type="submit" class="px-8 py-3 bg-indigo-600 hover:bg-indigo-700 text-white text-sm font-bold rounded-xl shadow-lg shadow-indigo-200 hover:shadow-indigo-300 transition flex items-center gap-2">
                            <i class="fa-solid fa-paper-plane"></i> Enviar Respostas
                        </button>
                    </div>
                </form>
            </div>
        </section>

        <!-- SECTION 3: BANCO DE DADOS BRUTOS (TABELA DE RESPOSTAS) -->
        <section id="tab-responses" class="hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200">
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 mb-6">
                    <div>
                        <h2 class="text-xl font-bold text-slate-900">Registro Individual de Respostas</h2>
                        <p class="text-xs text-slate-500">Tabela completa com todos os dados brutos coletados dos participantes.</p>
                    </div>
                    <button onclick="exportDataCSV()" class="px-4 py-2 bg-emerald-600 hover:bg-emerald-700 text-white text-xs font-semibold rounded-xl flex items-center gap-2 shadow-sm transition">
                        <i class="fa-solid fa-file-csv"></i> Exportar CSV
                    </button>
                </div>

                <div class="overflow-x-auto custom-scrollbar border border-slate-200 rounded-xl">
                    <table class="w-full text-left text-xs text-slate-600">
                        <thead class="bg-slate-50 text-slate-700 uppercase font-bold border-b border-slate-200">
                            <tr id="responses-table-head">
                <th class="p-3">#</th>
                <th class="p-3">Data/Hora</th>
                <th class="p-3">Idade</th>
                <th class="p-3 whitespace-nowrap" title="Rede social mais utilizada no dia a dia">Q1 (Rede Social Favorita)</th><th class="p-3 whitespace-nowrap" title="Estilo musical preferido">Q2 (Gênero Musical)</th><th class="p-3 whitespace-nowrap" title="Principal dispositivo utilizado para estudos e tarefas">Q3 (Dispositivo Principal)</th><th class="p-3 whitespace-nowrap" title="Principal meio de acesso a notícias e atualidades">Q4 (Fonte de Notícias)</th><th class="p-3 whitespace-nowrap" title="Área do conhecimento que pretende seguir no futuro">Q5 (Área Futura)</th><th class="p-3 whitespace-nowrap" title="Nível habitual de estresse em relação aos estudos escolares">Q6 (Nível de Estresse)</th><th class="p-3 whitespace-nowrap" title="Frequência de preocupação com o futuro profissional e vestibulares">Q7 (Preocupação com Futuro)</th><th class="p-3 whitespace-nowrap" title="Autoavaliação do desempenho escolar atual">Q8 (Desempenho Escolar)</th><th class="p-3 whitespace-nowrap" title="Grau de concordância: " a="" inteligência="" artificial="" trará="" impactos="" positivos="" para="" os="" jovens""="">Q9 (Impacto da IA)</th><th class="p-3 whitespace-nowrap" title="Frequência de prática de hábitos de saúde (hidratação, alimentação equilibrada)">Q10 (Hábitos Saudáveis)</th><th class="p-3 whitespace-nowrap" title="Quantidade de redes sociais diferentes acessadas diariamente">Q11 (Nº de Redes Usadas)</th><th class="p-3 whitespace-nowrap" title="Quantidade de livros lidos por ano (fora os de leitura obrigatória)">Q12 (Livros por Ano)</th><th class="p-3 whitespace-nowrap" title="Quantos dias por semana pratica esportes ou atividade física">Q13 (Dias de Exercício/Semana)</th><th class="p-3 whitespace-nowrap" title="Número de amigos próximos (de real confiança)">Q14 (Nº de Amigos Próximos)</th><th class="p-3 whitespace-nowrap" title="Horas médias de sono por noite nos dias de aula">Q15 (Horas de Sono/Noite)</th><th class="p-3 whitespace-nowrap" title="Tempo médio diário de uso de tela no smartphone (horas)">Q16 (Tempo de Tela Diário (h))</th><th class="p-3 whitespace-nowrap" title="Estimativa de gastos pessoais semanais com lazer/lanches (em R$)">Q17 (Gasto Semanal (R$))</th><th class="p-3 whitespace-nowrap" title="Altura aproximada (em metros)">Q18 (Altura (m))</th><th class="p-3 whitespace-nowrap" title="Horas semanais dedicadas a hobbies fora das telas (esporte, música, desenho, etc.)">Q19 (Hobbies Fora de Tela (h))</th><th class="p-3 whitespace-nowrap" title="Tempo de deslocamento diário até a escola (em minutos)">Q20 (Deslocamento Escola (min))</th>
            </tr>
                        </thead>
                        <tbody id="responses-table-body" class="divide-y divide-slate-100"><tr><td colspan="23" class="p-6 text-center text-slate-400">Nenhuma resposta registrada ainda.</td></tr></tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- SECTION 4: GUIA DE HOSPEDAGEM GRATUITA (ONLINE SHARE GUIDE) -->
        <section id="tab-hosting" class="hidden space-y-6 max-w-4xl mx-auto">
            <div class="bg-white rounded-2xl p-6 sm:p-8 shadow-sm border border-slate-200 space-y-6">
                <div class="border-b border-slate-200 pb-4">
                    <span class="text-xs font-bold uppercase tracking-wider text-emerald-600 bg-emerald-50 px-3 py-1 rounded-full">Passo a Passo</span>
                    <h2 class="text-2xl font-bold text-slate-900 mt-2">Como colocar esta pesquisa online grátis para todos</h2>
                    <p class="text-sm text-slate-500 mt-1">
                        Para que qualquer pessoa consiga abrir o link no celular ou computador de qualquer lugar, basta publicar este arquivo HTML em uma plataforma gratuita.
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <!-- Step 1 -->
                    <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200 space-y-3">
                        <div class="w-8 h-8 rounded-full bg-indigo-600 text-white font-bold flex items-center justify-center text-sm">1</div>
                        <h3 class="font-bold text-slate-800 text-sm">Baixar o Projeto</h3>
                        <p class="text-xs text-slate-600">Clique no botão abaixo para salvar o arquivo <code>index.html</code> no seu computador.</p>
                        <button onclick="downloadHTMLFile()" class="w-full py-2 bg-indigo-600 hover:bg-indigo-700 text-white rounded-xl text-xs font-bold shadow transition flex items-center justify-center gap-2">
                            <i class="fa-solid fa-download"></i> Baixar index.html
                        </button>
                    </div>

                    <!-- Step 2 -->
                    <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200 space-y-3">
                        <div class="w-8 h-8 rounded-full bg-indigo-600 text-white font-bold flex items-center justify-center text-sm">2</div>
                        <h3 class="font-bold text-slate-800 text-sm">Escolher a Hospedagem</h3>
                        <p class="text-xs text-slate-600">Recomendamos utilizar o <strong>Netlify Drop</strong> ou <strong>GitHub Pages</strong> (ambos 100% gratuitos e instantâneos).</p>
                        <a href="https://app.netlify.com/drop" target="_blank" class="w-full py-2 bg-emerald-600 hover:bg-emerald-700 text-white rounded-xl text-xs font-bold shadow transition flex items-center justify-center gap-2" rel="noopener noreferrer">
                            <i class="fa-solid fa-arrow-up-right-from-square"></i> Netlify Drop
                        </a>
                    </div>

                    <!-- Step 3 -->
                    <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200 space-y-3">
                        <div class="w-8 h-8 rounded-full bg-indigo-600 text-white font-bold flex items-center justify-center text-sm">3</div>
                        <h3 class="font-bold text-slate-800 text-sm">Arrastar e Compartilhar</h3>
                        <p class="text-xs text-slate-600">Arraste o arquivo baixado para a página do Netlify. Ele criará um link público na hora (ex: <code>https://pesquisa-teen.netlify.app</code>) para enviar aos alunos!</p>
                    </div>
                </div>

                <div class="p-4 bg-amber-50 border border-amber-200 rounded-xl flex items-start gap-3">
                    <i class="fa-solid fa-lightbulb text-amber-600 text-lg mt-0.5"></i>
                    <div class="text-xs text-amber-900 space-y-1">
                        <strong class="font-bold">Dica para a Apresentação Escolar / Acadêmica:</strong>
                        <p>O aplicativo já conta com o banco de dados sincronizado. Qualquer resposta enviada através do link publicado atualizará automaticamente o painel estatístico em tempo real!</p>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-slate-900 text-slate-400 py-6 text-xs text-center border-t border-slate-800">
        <div class="max-w-7xl mx-auto px-4 space-y-2">
            <p class="font-semibold text-slate-300">StatTeen © 2026 - Ferramenta Pedagógica de Análise Estatística</p>
            <p>Cobertura: Frequência Absoluta/Relativa, Média, Mediana, Moda, Desvio Padrão, Variância e Gráficos Dinâmicos (Setores, Linhas, Histogramas).</p>
        </div>
    </footer>

    <!-- JAVASCRIPT APP ENGINE WITH CLOUD STORAGE -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, addDoc, onSnapshot } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        /**
         * QUESTION DEFINITIONS & CLASSIFICATION (20 QUESTIONS)
         */
        const QUESTIONS = [
            // --- QUALITATIVAS NOMINAIS (Q1 a Q5) ---
            {
                id: 'q1',
                num: 1,
                type: 'NOMINAL',
                chartType: 'pie',
                title: 'Rede social mais utilizada no dia a dia',
                label: 'Rede Social Favorita',
                options: ['Instagram', 'TikTok', 'YouTube', 'WhatsApp', 'Discord', 'X (Twitter)']
            },
            {
                id: 'q2',
                num: 2,
                type: 'NOMINAL',
                chartType: 'pie',
                title: 'Estilo musical preferido',
                label: 'Gênero Musical',
                options: ['Funk', 'Pop', 'Trap / Rap', 'Sertanejo', 'Rock / Indie', 'K-Pop', 'Eletrônica']
            },
            {
                id: 'q3',
                num: 3,
                type: 'NOMINAL',
                chartType: 'pie',
                title: 'Principal dispositivo utilizado para estudos e tarefas',
                label: 'Dispositivo Principal',
                options: ['Smartphone', 'Notebook / PC', 'Tablet']
            },
            {
                id: 'q4',
                num: 4,
                type: 'NOMINAL',
                chartType: 'pie',
                title: 'Principal meio de acesso a notícias e atualidades',
                label: 'Fonte de Notícias',
                options: ['Redes Sociais', 'Portais de Notícias', 'YouTube / Podcasts', 'Televisão', 'Conversas Família/Amigos']
            },
            {
                id: 'q5',
                num: 5,
                type: 'NOMINAL',
                chartType: 'pie',
                title: 'Área do conhecimento que pretende seguir no futuro',
                label: 'Área Futura',
                options: ['Exatas e Tecnologia', 'Biológicas e Saúde', 'Humanas e Sociais', 'Artes e Comunicação', 'Ainda Não Sei']
            },

            // --- QUALITATIVAS ORDINAIS (Q6 a Q10) ---
            {
                id: 'q6',
                num: 6,
                type: 'ORDINAL',
                chartType: 'line',
                title: 'Nível habitual de estresse em relação aos estudos escolares',
                label: 'Nível de Estresse',
                options: ['1 - Muito Baixo', '2 - Baixo', '3 - Moderado', '4 - Alto', '5 - Muito Alto']
            },
            {
                id: 'q7',
                num: 7,
                type: 'ORDINAL',
                chartType: 'line',
                title: 'Frequência de preocupação com o futuro profissional e vestibulares',
                label: 'Preocupação com Futuro',
                options: ['Nunca', 'Raramente', 'Às Vezes', 'Frequentemente', 'Sempre']
            },
            {
                id: 'q8',
                num: 8,
                type: 'ORDINAL',
                chartType: 'line',
                title: 'Autoavaliação do desempenho escolar atual',
                label: 'Desempenho Escolar',
                options: ['Insuficiente', 'Regular', 'Bom', 'Muito Bom', 'Excelente']
            },
            {
                id: 'q9',
                num: 9,
                type: 'ORDINAL',
                chartType: 'line',
                title: 'Grau de concordância: "A Inteligência Artificial trará impactos positivos para os jovens"',
                label: 'Impacto da IA',
                options: ['Discordo Totalmente', 'Discordo Parcialmente', 'Neutro', 'Concordo Parcialmente', 'Concordo Totalmente']
            },
            {
                id: 'q10',
                num: 10,
                type: 'ORDINAL',
                chartType: 'line',
                title: 'Frequência de prática de hábitos de saúde (hidratação, alimentação equilibrada)',
                label: 'Hábitos Saudáveis',
                options: ['Raramente', 'Às Vezes', 'Frequência Moderada', 'Quase Sempre', 'Sempre']
            },

            // --- QUANTITATIVAS DISCRETAS (Q11 a Q15) ---
            {
                id: 'q11',
                num: 11,
                type: 'DISCRETA',
                chartType: 'bar',
                title: 'Quantidade de redes sociais diferentes acessadas diariamente',
                label: 'Nº de Redes Usadas',
                min: 1, max: 8, step: 1, unit: 'redes'
            },
            {
                id: 'q12',
                num: 12,
                type: 'DISCRETA',
                chartType: 'bar',
                title: 'Quantidade de livros lidos por ano (fora os de leitura obrigatória)',
                label: 'Livros por Ano',
                min: 0, max: 15, step: 1, unit: 'livros'
            },
            {
                id: 'q13',
                num: 13,
                type: 'DISCRETA',
                chartType: 'bar',
                title: 'Quantos dias por semana pratica esportes ou atividade física',
                label: 'Dias de Exercício/Semana',
                min: 0, max: 7, step: 1, unit: 'dias'
            },
            {
                id: 'q14',
                num: 14,
                type: 'DISCRETA',
                chartType: 'bar',
                title: 'Número de amigos próximos (de real confiança)',
                label: 'Nº de Amigos Próximos',
                min: 0, max: 10, step: 1, unit: 'amigos'
            },
            {
                id: 'q15',
                num: 15,
                type: 'DISCRETA',
                chartType: 'bar',
                title: 'Horas médias de sono por noite nos dias de aula',
                label: 'Horas de Sono/Noite',
                min: 4, max: 10, step: 1, unit: 'horas'
            },

            // --- QUANTITATIVAS CONTÍNUSA (Q16 a Q20) ---
            {
                id: 'q16',
                num: 16,
                type: 'CONTINUA',
                chartType: 'histogram',
                title: 'Tempo médio diário de uso de tela no smartphone (horas)',
                label: 'Tempo de Tela Diário (h)',
                min: 1.0, max: 14.0, step: 0.5, unit: 'h'
            },
            {
                id: 'q17',
                num: 17,
                type: 'CONTINUA',
                chartType: 'histogram',
                title: 'Estimativa de gastos pessoais semanais com lazer/lanches (em R$)',
                label: 'Gasto Semanal (R$)',
                min: 0.0, max: 200.0, step: 5.0, unit: 'R$'
            },
            {
                id: 'q18',
                num: 18,
                type: 'CONTINUA',
                chartType: 'histogram',
                title: 'Altura aproximada (em metros)',
                label: 'Altura (m)',
                min: 1.45, max: 2.05, step: 0.01, unit: 'm'
            },
            {
                id: 'q19',
                num: 19,
                type: 'CONTINUA',
                chartType: 'histogram',
                title: 'Horas semanais dedicadas a hobbies fora das telas (esporte, música, desenho, etc.)',
                label: 'Hobbies Fora de Tela (h)',
                min: 0.0, max: 25.0, step: 0.5, unit: 'h'
            },
            {
                id: 'q20',
                num: 20,
                type: 'CONTINUA',
                chartType: 'histogram',
                title: 'Tempo de deslocamento diário até a escola (em minutos)',
                label: 'Deslocamento Escola (min)',
                min: 5.0, max: 90.0, step: 5.0, unit: 'min'
            }
        ];

        // GLOBAL IN-MEMORY & CLOUD STORE
        let responsesStore = [];
        let activeFilter = 'ALL';
        let chartInstances = {};

        // Firebase References
        let db = null;
        let auth = null;
        let cloudUser = null;
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'stat-teen-app-default';

        // Make functions globally accessible for inline HTML event handlers
        window.switchTab = switchTab;
        window.filterDashboard = filterDashboard;
        window.handleFormSubmit = handleFormSubmit;
        window.toggleShareModal = toggleShareModal;
        window.copyShareLink = copyShareLink;
        window.generateMockResponses = generateMockResponses;
        window.exportDataJSON = exportDataJSON;
        window.exportDataCSV = exportDataCSV;
        window.resetDataConfirmation = resetDataConfirmation;
        window.downloadHTMLFile = downloadHTMLFile;

        // INITIALIZATION
        window.onload = async function() {
            initLocalDataStore();
            renderSurveyForm();
            renderDashboard();
            updateShareLinkAndQR();
            await initCloudSync();
        };

        // --- FIREBASE CLOUD SYNC INITIALIZATION ---
        async function initCloudSync() {
            if (typeof __firebase_config === 'undefined') {
                console.log("Firebase Config não detectado. Operando em modo offline local.");
                return;
            }

            try {
                const firebaseConfig = JSON.parse(__firebase_config);
                const app = initializeApp(firebaseConfig);
                auth = getAuth(app);
                db = getFirestore(app);

                const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;
                if (initialAuthToken) {
                    const cred = await signInWithCustomToken(auth, initialAuthToken);
                    cloudUser = cred.user;
                } else {
                    const cred = await signInAnonymously(auth);
                    cloudUser = cred.user;
                }

                if (!cloudUser) return;

                // Listen to public data collection in real-time (Rule 1)
                const colRef = collection(db, 'artifacts', appId, 'public', 'data', 'responses');
                onSnapshot(colRef, (snapshot) => {
                    const cloudList = [];
                    snapshot.forEach(doc => {
                        cloudList.push({ id: doc.id, ...doc.data() });
                    });
                    if (cloudList.length > 0) {
                        responsesStore = cloudList;
                        saveDataStoreLocallyOnly();
                        renderDashboard();
                        renderResponsesTable();
                    }
                }, (err) => {
                    console.error("Erro na escuta do banco em nuvem:", err);
                });

            } catch(e) {
                console.warn("Falha ao inicializar banco online:", e);
            }
        }

        // --- DATA STORE MANAGERS ---
        function initLocalDataStore() {
            const saved = localStorage.getItem('stat_teen_responses_v1');
            if (saved) {
                try {
                    responsesStore = JSON.parse(saved);
                } catch(e) {
                    responsesStore = [];
                }
            }
            if (responsesStore.length === 0) {
                responsesStore = generateSeedResponses(20);
                saveDataStoreLocallyOnly();
            }
        }

        function saveDataStoreLocallyOnly() {
            localStorage.setItem('stat_teen_responses_v1', JSON.stringify(responsesStore));
            const badge = document.getElementById('response-count-badge');
            if (badge) badge.innerText = `Total: ${responsesStore.length} Respostas`;
        }

        async function saveResponseToCloud(newResp) {
            saveDataStoreLocallyOnly();
            if (db && cloudUser) {
                try {
                    const colRef = collection(db, 'artifacts', appId, 'public', 'data', 'responses');
                    await addDoc(colRef, newResp);
                } catch(e) {
                    console.error("Erro ao salvar no banco em nuvem:", e);
                }
            }
        }

        function generateSeedResponses(count) {
            const seeds = [];
            const now = new Date();

            for(let i=0; i<count; i++) {
                const respTime = new Date(now.getTime() - Math.random() * 86400000 * 7).toLocaleString('pt-BR');
                seeds.push({
                    id: 'resp_' + Math.random().toString(36).substring(2, 9),
                    timestamp: respTime,
                    age: Math.floor(Math.random() * 3) + 15,
                    q1: getRandomItem(['Instagram', 'TikTok', 'Instagram', 'TikTok', 'YouTube', 'WhatsApp', 'Discord', 'X (Twitter)']),
                    q2: getRandomItem(['Funk', 'Trap / Rap', 'Pop', 'Sertanejo', 'Rock / Indie', 'K-Pop', 'Funk']),
                    q3: getRandomItem(['Smartphone', 'Smartphone', 'Notebook / PC', 'Tablet']),
                    q4: getRandomItem(['Redes Sociais', 'Redes Sociais', 'YouTube / Podcasts', 'Portais de Notícias', 'Conversas Família/Amigos']),
                    q5: getRandomItem(['Exatas e Tecnologia', 'Biológicas e Saúde', 'Humanas e Sociais', 'Artes e Comunicação', 'Ainda Não Sei']),
                    q6: getRandomItem(['1 - Muito Baixo', '2 - Baixo', '3 - Moderado', '4 - Alto', '4 - Alto', '5 - Muito Alto']),
                    q7: getRandomItem(['Raramente', 'Às Vezes', 'Frequentemente', 'Frequentemente', 'Sempre']),
                    q8: getRandomItem(['Regular', 'Bom', 'Bom', 'Muito Bom', 'Excelente']),
                    q9: getRandomItem(['Discordo Parcialmente', 'Neutro', 'Concordo Parcialmente', 'Concordo Totalmente']),
                    q10: getRandomItem(['Raramente', 'Às Vezes', 'Frequência Moderada', 'Quase Sempre', 'Sempre']),
                    q11: Math.floor(Math.random() * 4) + 2,
                    q12: Math.floor(Math.random() * 6),
                    q13: Math.floor(Math.random() * 6),
                    q14: Math.floor(Math.random() * 6) + 1,
                    q15: Math.floor(Math.random() * 4) + 5,
                    q16: parseFloat((Math.random() * 6 + 3).toFixed(1)),
                    q17: parseFloat((Math.random() * 80 + 20).toFixed(2)),
                    q18: parseFloat((Math.random() * 0.35 + 1.55).toFixed(2)),
                    q19: parseFloat((Math.random() * 10 + 2).toFixed(1)),
                    q20: parseFloat((Math.random() * 45 + 10).toFixed(0))
                });
            }
            return seeds;
        }

        function getRandomItem(arr) {
            return arr[Math.floor(Math.random() * arr.length)];
        }

        async function generateMockResponses(num = 5) {
            const newSeeds = generateSeedResponses(num);
            for (const item of newSeeds) {
                responsesStore.push(item);
                if (db && cloudUser) {
                    await saveResponseToCloud(item);
                }
            }
            saveDataStoreLocallyOnly();
            renderDashboard();
            renderResponsesTable();
            showToast(`+${num} respostas simuladas adicionadas com sucesso!`);
        }

        function resetDataConfirmation() {
            if (responsesStore.length === 0) return;
            responsesStore = [];
            saveDataStoreLocallyOnly();
            renderDashboard();
            renderResponsesTable();
            showToast('Banco de dados zerado.', 'info');
        }

        // --- SHARE LINK & QR CODE GENERATOR ---
        function updateShareLinkAndQR() {
            const currentUrl = window.location.href;
            const input = document.getElementById('share-link-input');
            if (input) input.value = currentUrl;

            const qrContainer = document.getElementById('qr-code-container');
            if (qrContainer) {
                const qrApiUrl = `https://api.qrserver.com/v1/create-qr-code/?size=120x120&data=${encodeURIComponent(currentUrl)}`;
                qrContainer.innerHTML = `<img src="${qrApiUrl}" alt="QR Code Pesquisa" class="w-28 h-28 object-contain">`;
            }
        }

        function downloadHTMLFile() {
            const htmlContent = "<!DOCTYPE html>\n" + document.documentElement.outerHTML;
            const blob = new Blob([htmlContent], { type: 'text/html;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'pesquisa_estatistica_teen_15_17.html';
            a.click();
            URL.revokeObjectURL(url);
            showToast('Arquivo index.html baixado para publicação!');
        }

        // --- TAB NAVIGATION ---
        function switchTab(tabName) {
            ['dashboard', 'survey', 'responses', 'hosting'].forEach(t => {
                const el = document.getElementById(`tab-${t}`);
                const btn = document.getElementById(`tab-btn-${t}`);
                if (!el || !btn) return;
                if (t === tabName) {
                    el.classList.remove('hidden');
                    btn.classList.add('bg-indigo-700', 'text-white', 'shadow');
                    btn.classList.remove('text-indigo-200', 'hover:bg-indigo-800');
                } else {
                    el.classList.add('hidden');
                    btn.classList.remove('bg-indigo-700', 'text-white', 'shadow');
                    btn.classList.add('text-indigo-200', 'hover:bg-indigo-800');
                }
            });

            if (tabName === 'responses') {
                renderResponsesTable();
            } else if (tabName === 'dashboard') {
                renderDashboard();
            }
        }

        // --- RENDER FORMULÁRIO DE PESQUISA ---
        function renderSurveyForm() {
            const container = document.getElementById('survey-questions-list');
            if (!container) return;
            let html = '';

            html += `
                <div class="p-5 bg-indigo-50/60 border border-indigo-100 rounded-2xl">
                    <label class="block font-bold text-slate-800 text-sm mb-2">Qual é a sua idade atual?</label>
                    <div class="flex gap-4">
                        ${[15, 16, 17].map(age => `
                            <label class="flex items-center gap-2 bg-white px-4 py-2 border border-slate-300 rounded-xl cursor-pointer hover:border-indigo-500 font-semibold text-xs">
                                <input type="radio" name="age" value="${age}" required ${age===16?'checked':''}>
                                <span>${age} anos</span>
                            </label>
                        `).join('')}
                    </div>
                </div>
            `;

            QUESTIONS.forEach(q => {
                let badgeColor = '';
                let badgeText = '';
                if(q.type === 'NOMINAL') { badgeColor = 'bg-blue-100 text-blue-800'; badgeText = 'Qualitativa Nominal'; }
                else if(q.type === 'ORDINAL') { badgeColor = 'bg-purple-100 text-purple-800'; badgeText = 'Qualitativa Ordinal'; }
                else if(q.type === 'DISCRETA') { badgeColor = 'bg-amber-100 text-amber-800'; badgeText = 'Quantitativa Discreta'; }
                else { badgeColor = 'bg-emerald-100 text-emerald-800'; badgeText = 'Quantitativa Contínua'; }

                html += `
                    <div class="p-5 bg-white border border-slate-200 rounded-2xl shadow-sm space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold text-slate-400">Pergunta ${q.num} de 20</span>
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded-full ${badgeColor}">${badgeText}</span>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">${q.title}</h3>
                `;

                if (q.type === 'NOMINAL' || q.type === 'ORDINAL') {
                    html += `<div class="grid grid-cols-1 sm:grid-cols-2 gap-2 pt-1">`;
                    q.options.forEach(opt => {
                        html += `
                            <label class="flex items-center gap-2 bg-slate-50 border border-slate-200 hover:border-indigo-400 hover:bg-indigo-50/30 px-3 py-2.5 rounded-xl cursor-pointer transition text-xs">
                                <input type="radio" name="${q.id}" value="${opt}" required class="text-indigo-600 focus:ring-indigo-500">
                                <span class="text-slate-700 font-medium">${opt}</span>
                            </label>
                        `;
                    });
                    html += `</div>`;
                } else if (q.type === 'DISCRETA') {
                    html += `
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="${q.id}" min="${q.min}" max="${q.max}" step="${q.step}" required
                                class="w-32 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none"
                                placeholder="Ex: ${Math.floor((q.min+q.max)/2)}">
                            <span class="text-xs font-medium text-slate-500">${q.unit}</span>
                        </div>
                    `;
                } else if (q.type === 'CONTINUA') {
                    html += `
                        <div class="flex items-center gap-3 pt-1">
                            <input type="number" name="${q.id}" min="${q.min}" max="${q.max}" step="${q.step}" required
                                class="w-36 bg-slate-50 border border-slate-300 rounded-xl px-3 py-2 text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-indigo-500 focus:outline-none"
                                placeholder="Ex: ${((q.min+q.max)/2).toFixed(1)}">
                            <span class="text-xs font-medium text-slate-500">${q.unit}</span>
                        </div>
                    `;
                }

                html += `</div>`;
            });

            container.innerHTML = html;
        }

        // --- SUBMIT DO FORMULÁRIO ---
        async function handleFormSubmit(e) {
            e.preventDefault();
            const form = e.target;
            const formData = new FormData(form);

            const newResp = {
                id: 'resp_' + Math.random().toString(36).substring(2, 9),
                timestamp: new Date().toLocaleString('pt-BR'),
                age: parseInt(formData.get('age'))
            };

            QUESTIONS.forEach(q => {
                const val = formData.get(q.id);
                if (q.type === 'DISCRETA' || q.type === 'CONTINUA') {
                    newResp[q.id] = parseFloat(val);
                } else {
                    newResp[q.id] = val;
                }
            });

            responsesStore.push(newResp);
            await saveResponseToCloud(newResp);
            form.reset();

            showToast('Resposta registrada com sucesso! Estatísticas atualizadas.');
            switchTab('dashboard');
        }

        // --- ESTATÍSTICA MATEMÁTICA ENGINE ---
        function calculateStatistics(q, dataList) {
            const values = dataList.map(d => d[q.id]).filter(v => v !== undefined && v !== null);
            const n = values.length;

            if (n === 0) {
                return { n: 0, frequencies: [], mean: null, median: null, mode: null, variance: null, stdDev: null, min: 0, max: 0 };
            }

            if (q.type === 'NOMINAL' || q.type === 'ORDINAL') {
                const freqMap = {};
                q.options.forEach(opt => freqMap[opt] = 0);
                values.forEach(v => {
                    freqMap[v] = (freqMap[v] || 0) + 1;
                });

                let accum = 0;
                const frequencies = q.options.map(opt => {
                    const fi = freqMap[opt] || 0;
                    const fr = n > 0 ? (fi / n) : 0;
                    const pct = (fr * 100).toFixed(1);
                    accum += fi;
                    const Fi = accum;
                    const FrPct = ((Fi / n) * 100).toFixed(1);
                    return { category: opt, fi, fr, pct, Fi, FrPct };
                });

                // Mode calculation
                let maxFi = -1;
                let modes = [];
                frequencies.forEach(f => {
                    if (f.fi > maxFi) {
                        maxFi = f.fi;
                        modes = [f.category];
                    } else if (f.fi === maxFi && maxFi > 0) {
                        modes.push(f.category);
                    }
                });

                // Median calculation for Ordinal
                let medianVal = 'N/A';
                if (q.type === 'ORDINAL') {
                    const half = Math.ceil(n / 2);
                    let runningSum = 0;
                    for (let f of frequencies) {
                        runningSum += f.fi;
                        if (runningSum >= half) {
                            medianVal = f.category;
                            break;
                        }
                    }
                }

                return {
                    n,
                    frequencies,
                    mode: modes.join(', '),
                    median: medianVal,
                    mean: 'N/A',
                    variance: 'N/A',
                    stdDev: 'N/A'
                };
            }

            // QUANTITATIVAS (DISCRETA OU CONTÍNUA)
            const nums = values.map(v => Number(v)).sort((a, b) => a - b);
            const sum = nums.reduce((acc, curr) => acc + curr, 0);
            const mean = sum / n;

            // Median
            let median = 0;
            const mid = Math.floor(n / 2);
            if (n % 2 !== 0) {
                median = nums[mid];
            } else {
                median = (nums[mid - 1] + nums[mid]) / 2;
            }

            // Mode
            const counts = {};
            nums.forEach(x => counts[x] = (counts[x] || 0) + 1);
            let maxCount = 0;
            let modes = [];
            for (let k in counts) {
                if (counts[k] > maxCount) {
                    maxCount = counts[k];
                    modes = [Number(k)];
                } else if (counts[k] === maxCount) {
                    modes.push(Number(k));
                }
            }
            const modeStr = (maxCount === 1 && nums.length > 1) ? 'Amodal' : modes.join(', ');

            // Sample Variance (s²) & Standard Deviation (s)
            let sumSqDiff = 0;
            nums.forEach(x => {
                sumSqDiff += Math.pow(x - mean, 2);
            });
            const variance = n > 1 ? (sumSqDiff / (n - 1)) : 0;
            const stdDev = Math.sqrt(variance);

            const minVal = nums[0];
            const maxVal = nums[n - 1];

            let frequencies = [];

            if (q.type === 'DISCRETA') {
                const distValues = [...new Set(nums)].sort((a,b)=>a-b);
                let accum = 0;
                frequencies = distValues.map(val => {
                    const fi = counts[val];
                    const fr = fi / n;
                    const pct = (fr * 100).toFixed(1);
                    accum += fi;
                    return {
                        category: `${val} ${q.unit}`,
                        rawVal: val,
                        fi,
                        fr,
                        pct,
                        Fi: accum,
                        FrPct: ((accum / n) * 100).toFixed(1)
                    };
                });
            } else if (q.type === 'CONTINUA') {
                const numClasses = 5;
                const range = (maxVal - minVal) || 1;
                const classWidth = range / numClasses;

                let accum = 0;
                for (let i = 0; i < numClasses; i++) {
                    const lower = minVal + i * classWidth;
                    const upper = lower + classWidth;
                    const isLast = (i === numClasses - 1);
                    
                    const fi = nums.filter(x => isLast ? (x >= lower && x <= upper) : (x >= lower && x < upper)).length;
                    const fr = fi / n;
                    const pct = (fr * 100).toFixed(1);
                    accum += fi;
                    const xi = (lower + upper) / 2;

                    frequencies.push({
                        category: `[${lower.toFixed(1)} ├ ${upper.toFixed(1)})`,
                        midpoint: xi.toFixed(1),
                        fi,
                        fr,
                        pct,
                        Fi: accum,
                        FrPct: ((accum / n) * 100).toFixed(1)
                    });
                }
            }

            return {
                n,
                frequencies,
                mean: mean.toFixed(2),
                median: median.toFixed(2),
                mode: modeStr,
                variance: variance.toFixed(2),
                stdDev: stdDev.toFixed(2),
                min: minVal,
                max: maxVal
            };
        }

        // --- DASHBOARD RENDERER ---
        function filterDashboard(type) {
            activeFilter = type;
            ['ALL', 'NOMINAL', 'ORDINAL', 'DISCRETA', 'CONTINUA'].forEach(t => {
                const btn = document.getElementById(`filter-btn-${t}`);
                if (!btn) return;
                if (t === type) {
                    btn.className = "px-3 py-1.5 rounded-lg font-semibold bg-indigo-600 text-white shadow-sm border border-indigo-600";
                } else {
                    btn.className = "px-3 py-1.5 rounded-lg font-semibold text-slate-600 hover:bg-white hover:shadow-sm";
                }
            });
            renderDashboard();
        }

        function renderDashboard() {
            const container = document.getElementById('questions-dashboard-container');
            if (!container) return;
            container.innerHTML = '';

            const filteredQuestions = QUESTIONS.filter(q => activeFilter === 'ALL' || q.type === activeFilter);

            filteredQuestions.forEach(q => {
                const stats = calculateStatistics(q, responsesStore);

                const card = document.createElement('div');
                card.className = "bg-white rounded-2xl p-6 shadow-sm border border-slate-200/90 space-y-6 transition-all hover:shadow-md";

                let typeBadge = '';
                if(q.type === 'NOMINAL') typeBadge = '<span class="bg-blue-100 text-blue-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Nominal</span>';
                else if(q.type === 'ORDINAL') typeBadge = '<span class="bg-purple-100 text-purple-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Qualitativa Ordinal</span>';
                else if(q.type === 'DISCRETA') typeBadge = '<span class="bg-amber-100 text-amber-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Discreta</span>';
                else typeBadge = '<span class="bg-emerald-100 text-emerald-800 text-[11px] font-bold px-2.5 py-1 rounded-full uppercase">Quantitativa Contínua</span>';

                card.innerHTML = `
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2 border-b border-slate-100 pb-4">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-slate-400 text-xs">Pergunta #${q.num}</span>
                                ${typeBadge}
                            </div>
                            <h3 class="text-lg font-bold text-slate-900 mt-1">${q.title}</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Amostra (n)</span>
                            <span class="text-base font-extrabold text-slate-800">${stats.n}</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Média ($\bar{x}$)</span>
                            <span class="text-base font-extrabold ${stats.mean !== 'N/A' ? 'text-indigo-600' : 'text-slate-400'}">${stats.mean !== 'N/A' ? stats.mean + ' ' + (q.unit||'') : 'N/A'}</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Mediana ($Md$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block">${stats.median}</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Moda ($Mo$)</span>
                            <span class="text-base font-extrabold text-slate-800 truncate block" title="${stats.mode}">${stats.mode}</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Variância ($s^2$)</span>
                            <span class="text-base font-extrabold ${stats.variance !== 'N/A' ? 'text-purple-600' : 'text-slate-400'}">${stats.variance}</span>
                        </div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100">
                            <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider block">Desvio Padrão ($s$)</span>
                            <span class="text-base font-extrabold ${stats.stdDev !== 'N/A' ? 'text-emerald-600' : 'text-slate-400'}">${stats.stdDev}</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                        <div class="lg:col-span-6 overflow-x-auto custom-scrollbar">
                            <span class="text-xs font-bold text-slate-500 mb-2 block">Tabela de Frequência Absoluta e Relativa</span>
                            <table class="w-full text-left text-xs border border-slate-200 rounded-xl overflow-hidden">
                                <thead class="bg-slate-100 text-slate-700 font-bold border-b border-slate-200 uppercase text-[10px]">
                                    <tr>
                                        <th class="p-2.5">Classe / Categoria</th>
                                        <th class="p-2.5 text-center">Freq. Absoluta ($f_i$)</th>
                                        <th class="p-2.5 text-center">Freq. Relativa ($f_r\%$)</th>
                                        <th class="p-2.5 text-center">Acumulada ($F_i$)</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-100">
                                    ${stats.frequencies.map(f => `
                                        <tr class="hover:bg-slate-50/80 transition">
                                            <td class="p-2.5 font-semibold text-slate-700">${f.category}</td>
                                            <td class="p-2.5 text-center font-extrabold text-indigo-700">${f.fi}</td>
                                            <td class="p-2.5 text-center font-bold text-slate-600">${f.pct}%</td>
                                            <td class="p-2.5 text-center text-slate-500">${f.Fi}</td>
                                        </tr>
                                    `).join('')}
                                </tbody>
                                <tfoot class="bg-slate-50 font-bold border-t border-slate-200 text-slate-800">
                                    <tr>
                                        <td class="p-2.5 uppercase">Total ($\sum$)</td>
                                        <td class="p-2.5 text-center">${stats.n}</td>
                                        <td class="p-2.5 text-center">100%</td>
                                        <td class="p-2.5 text-center">-</td>
                                    </tr>
                                </tfoot>
                            </table>
                        </div>

                        <div class="lg:col-span-6 flex flex-col items-center justify-center min-h-[260px] bg-slate-50/50 p-4 rounded-2xl border border-slate-100 relative">
                            <span class="text-xs font-bold text-slate-500 mb-1 self-start">
                                Visualização: ${getChartTypeName(q.chartType)}
                            </span>
                            <div class="w-full h-64 relative flex items-center justify-center">
                                <canvas id="chart-canvas-${q.id}"></canvas>
                            </div>
                        </div>
                    </div>
                `;

                container.appendChild(card);
                setTimeout(() => buildQuestionChart(q, stats), 50);
            });
        }

        function getChartTypeName(chartType) {
            if(chartType === 'pie') return 'Gráfico de Setores (Pizza)';
            if(chartType === 'line') return 'Gráfico de Linhas (Tendência)';
            if(chartType === 'bar') return 'Gráfico de Barras Discretas';
            if(chartType === 'histogram') return 'Histograma de Frequências';
            return 'Gráfico Estatístico';
        }

        // --- CHART BUILDER ENGINE ---
        function buildQuestionChart(q, stats) {
            const canvas = document.getElementById(`chart-canvas-${q.id}`);
            if (!canvas) return;

            if (chartInstances[q.id]) {
                chartInstances[q.id].destroy();
            }

            const ctx = canvas.getContext('2d');
            const labels = stats.frequencies.map(f => f.category);
            const dataValues = stats.frequencies.map(f => f.fi);

            const colors = [
                '#6366f1', '#3b82f6', '#10b981', '#f59e0b', '#ec4899', 
                '#8b5cf6', '#14b8a6', '#f97316', '#06b6d4', '#64748b'
            ];

            let chartConfig = {};

            if (q.chartType === 'pie') {
                chartConfig = {
                    type: 'doughnut',
                    data: {
                        labels: labels,
                        datasets: [{
                            data: dataValues,
                            backgroundColor: colors.slice(0, labels.length),
                            borderWidth: 2,
                            borderColor: '#ffffff'
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: { position: 'bottom', labels: { boxWidth: 12, font: { size: 10 } } }
                        }
                    }
                };
            } else if (q.chartType === 'line') {
                chartConfig = {
                    type: 'line',
                    data: {
                        labels: labels,
                        datasets: [{
                            label: 'Frequência (fᵢ)',
                            data: dataValues,
                            borderColor: '#4f46e5',
                            backgroundColor: 'rgba(79, 70, 229, 0.15)',
                            fill: true,
                            tension: 0.35,
                            pointRadius: 6,
                            pointBackgroundColor: '#4338ca'
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: { legend: { display: false } },
                        scales: {
                            y: { beginAtZero: true, ticks: { precision: 0 } },
                            x: { ticks: { font: { size: 10 } } }
                        }
                    }
                };
            } else if (q.chartType === 'histogram') {
                chartConfig = {
                    type: 'bar',
                    data: {
                        labels: labels,
                        datasets: [{
                            label: 'Frequência Absoluta (fᵢ)',
                            data: dataValues,
                            backgroundColor: 'rgba(16, 185, 129, 0.75)',
                            borderColor: '#059669',
                            borderWidth: 1.5,
                            barPercentage: 1.0,
                            categoryPercentage: 1.0
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: { legend: { display: false } },
                        scales: {
                            y: { beginAtZero: true, ticks: { precision: 0 } },
                            x: { ticks: { font: { size: 9 } } }
                        }
                    }
                };
            } else {
                chartConfig = {
                    type: 'bar',
                    data: {
                        labels: labels,
                        datasets: [{
                            label: 'Quantidade de Respostas',
                            data: dataValues,
                            backgroundColor: 'rgba(245, 158, 11, 0.75)',
                            borderColor: '#d97706',
                            borderWidth: 1,
                            borderRadius: 6
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: { legend: { display: false } },
                        scales: {
                            y: { beginAtZero: true, ticks: { precision: 0 } }
                        }
                    }
                };
            }

            chartInstances[q.id] = new Chart(ctx, chartConfig);
        }

        // --- RAW DATA TABLE RENDERER ---
        function renderResponsesTable() {
            const head = document.getElementById('responses-table-head');
            const body = document.getElementById('responses-table-body');
            if (!head || !body) return;

            head.innerHTML = `
                <th class="p-3">#</th>
                <th class="p-3">Data/Hora</th>
                <th class="p-3">Idade</th>
                ${QUESTIONS.map(q => `<th class="p-3 whitespace-nowrap" title="${q.title}">Q${q.num} (${q.label})</th>`).join('')}
            `;

            if (responsesStore.length === 0) {
                body.innerHTML = `<tr><td colspan="${QUESTIONS.length + 3}" class="p-6 text-center text-slate-400">Nenhuma resposta registrada ainda.</td></tr>`;
                return;
            }

            body.innerHTML = responsesStore.map((r, idx) => `
                <tr class="hover:bg-slate-50 transition">
                    <td class="p-3 font-bold text-slate-400">${idx + 1}</td>
                    <td class="p-3 whitespace-nowrap text-slate-500">${r.timestamp}</td>
                    <td class="p-3 font-semibold text-indigo-600">${r.age} anos</td>
                    ${QUESTIONS.map(q => `<td class="p-3 whitespace-nowrap text-slate-700">${r[q.id] !== undefined ? r[q.id] : '-'}</td>`).join('')}
                </tr>
            `).join('');
        }

        // --- EXPORT & SHARE UTILITIES ---
        function toggleShareModal() {
            const modal = document.getElementById('share-modal');
            if (modal) {
                modal.classList.toggle('hidden');
                if (!modal.classList.contains('hidden')) {
                    updateShareLinkAndQR();
                }
            }
        }

        function copyShareLink() {
            const input = document.getElementById('share-link-input');
            if (input) {
                input.select();
                document.execCommand('copy');
                showToast('Link da pesquisa copiado para a área de transferência!');
            }
        }

        function exportDataJSON() {
            const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(responsesStore, null, 2));
            const downloadAnchor = document.createElement('a');
            downloadAnchor.setAttribute("href", dataStr);
            downloadAnchor.setAttribute("download", `pesquisa_adolescentes_dados_${new Date().toISOString().slice(0,10)}.json`);
            document.body.appendChild(downloadAnchor);
            downloadAnchor.click();
            downloadAnchor.remove();
            showToast('Arquivo JSON de dados exportado!');
        }

        function exportDataCSV() {
            if (responsesStore.length === 0) {
                showToast('Não há dados para exportar!', 'warning');
                return;
            }
            let csv = 'ID,DataHora,Idade,' + QUESTIONS.map(q => `Q${q.num}_${q.label.replace(/,/g, '')}`).join(',') + '\n';
            responsesStore.forEach(r => {
                let row = `"${r.id}","${r.timestamp}",${r.age},`;
                row += QUESTIONS.map(q => `"${r[q.id]}"`).join(',');
                csv += row + '\n';
            });

            const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `pesquisa_adolescentes_respostas_${new Date().toISOString().slice(0,10)}.csv`;
            a.click();
            URL.revokeObjectURL(url);
            showToast('Arquivo CSV baixado!');
        }

        // --- TOAST NOTIFICATIONS ---
        function showToast(message, type = 'success') {
            const container = document.getElementById('toast-container');
            if (!container) return;
            const toast = document.createElement('div');
            
            let bgClass = 'bg-slate-900 text-white';
            let icon = 'fa-check-circle text-emerald-400';
            if (type === 'info') icon = 'fa-info-circle text-blue-400';
            if (type === 'warning') icon = 'fa-exclamation-triangle text-amber-400';

            toast.className = `${bgClass} px-4 py-3 rounded-xl shadow-xl flex items-center space-x-3 text-xs font-semibold transform transition-all duration-300 opacity-0 translate-y-2`;
            toast.innerHTML = `<i class="fa-solid ${icon} text-base"></i><span>${message}</span>`;
            
            container.appendChild(toast);
            
            setTimeout(() => {
                toast.classList.remove('opacity-0', 'translate-y-2');
            }, 10);

            setTimeout(() => {
                toast.classList.add('opacity-0', 'translate-y-2');
                setTimeout(() => toast.remove(), 300);
            }, 3500);
        }
    </script>

</body></html>
