A gist of Server Side Rendering and why should we implement it.
-----------------------------------------------
Server-side rendering allows you to pre-render the initial state of your React components server-side. This speeds up First Contentful Paint as users do not stare at a blank screen waiting for all the JavaScript to load before seeing the content. When the Javascript is ready, it takes over the app. Also, from SEO standpoint, the crawlers are not that advanced to be relied upon for SEO when it comes to Javascript. Server side rendering takes care of that [might-impact-seo](https://www.onely.com/blog/javascript-seo-backfire-hulu-com-case-study/) concern.

The implications of Server Side Rendering
-------------------------------------
When you server render your page, you hydrate it client side. This Client side hydration can be really [costly](https://addyosmani.com/blog/rehydration/) on the First Input Delay and [Total Blocking Time](https://web.dev/tbt/) aspects of Web performance. The React team is already working on Partial hydration and Selective hydration which is exciting to know. 
However it's possible to implement it today with the help of some clever workarounds.

```js
import React from 'react';

/**
 * @description A Higher Order Component to bail out hydration phase,
                and renders when browser gets Idle time to execute it 
                or the user interacts with it (whichever is first)
 * @param {*} WrappedComponent 
 * @param {*} ComponentId 
 * @see{https://philipwalton.com/articles/idle-until-urgent/} - Idle Until Urgent : Philip Walton
 */
export function idleUntilUrgent(WrappedComponent, ComponentId) {
    class IdleUntilUrgent extends React.Component {
        constructor(props) {
            super(props);
            this.renderChild = false;
            this.firstRender = true;
            this.callbackId = null;
        }

        shouldComponentUpdate(nextProps, nextState)
        {
            return (this.props != nextProps) || (nextState && nextState.renderChild);
        }

        enqueueIdleRender = () => {
            requestIdleCallback(() => {
                const root = document.getElementById(ComponentId);
                this.setState({
                    renderChild : true
                })
            }, {timeout : 250});
        }

        urgentRender = () => {
            this.setState({
                renderChild : true
            })
        }    

        render = () => {

            if(typeof window !== "undefined" && this.firstRender)
            {
                    this.firstRender = false;
                    this.enqueueIdleRender();
                    return(
                    <div
                        dangerouslySetInnerHTML={{ __html: "" }}
                        suppressHydrationWarning = {true}
                        onClick = {this.urgentRender} 
                    />
                    )
                }
                else
                {
                    // Cancel the already scheduled render, if any
                    this.callbackId && cancelIdleCallback(this.callbackId); 
                    return <WrappedComponent {...this.props} />;
                }
            }
        };
    const wrappedComponentName = WrappedComponent.displayName || WrappedComponent.name || 'Component';
    IdleUntilUrgent.displayName = `IdleUntilUrgent (${wrappedComponentName})`;
    return IdleUntilUrgent;
}
```
