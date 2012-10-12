## RHStatusItemView
An NSStatusItem hosted view that supports handling both left and right click actions, menus and showing an image / alternateImage pair.


## Usage Example
<pre>
#import "RHStatusItemView.h"

@property (retain) IBOutlet NSMenu *statusMenu; //Created in MainMenu.nib 

//create the status item
NSStatusItem *statusItem = [[NSStatusBar systemStatusBar] statusItemWithLength:24];
[statusItem setHighlightMode:YES];

//create our custom view to be hosted inside the status item
RHStatusItemView *statusView = [[[RHStatusItemView alloc] initWithStatusBarItem:statusItem] autorelease];

[statusItem setView:statusView];

[statusView setToolTip:@"AppName"];        
[statusView setMenu:statusMenu];

[statusView setImage:[NSImage imageNamed:@"MenuIcon"]];
[statusView setAlternateImage:[NSImage imageNamed:@"MenuIconSelected"]];

</pre>

![Example Status Item.](https://github.com/heardrwt/RHStatusItemView/raw/master/RHStatusItemView.png )


## RHStatusItemView Interface
<pre>
@interface RHStatusItemView : NSControl {
}

@property (nonatomic, assign) NSStatusItem *statusItem; //should never be nil

@property (nonatomic, retain) NSImage *image;
@property (nonatomic, retain) NSImage *alternateImage; 

@property (nonatomic, retain) id target;
@property (nonatomic, assign) SEL action;       //if no action specified, we will try and pop up menu if set.
@property (nonatomic, assign) SEL rightAction;  //if no rightAction specified, we will try and pop up, in order rightMenu, menu.

@property (nonatomic, retain) NSMenu *menu;
@property (nonatomic, retain) NSMenu *rightMenu;

-(id)initWithStatusBarItem:(NSStatusItem*)statusItem; //designated initializer

-(void)popUpMenu; //pops up the currently stored menu
-(void)popUpRightMenu; //if right menu is set, pops up right menu
-(void)popUpMenu:(NSMenu*)menu; //pops up the passed menu

@end
</pre>

## Licence
Released under the Modified BSD License. 
(Attribution Required)
<pre>
RHStatusItemView

Copyright (c) 2012 Richard Heard. All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions
are met:
1. Redistributions of source code must retain the above copyright
notice, this list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright
notice, this list of conditions and the following disclaimer in the
documentation and/or other materials provided with the distribution.
3. The name of the author may not be used to endorse or promote products
derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY EXPRESS OR
IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES
OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED.
IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY DIRECT, INDIRECT,
INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT
NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF
THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
</pre>


### Version Support
This Framework code compiles and has been tested on OS X 10.7 - 10.8

