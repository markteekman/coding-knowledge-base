
> _**NOTE:** When we talk about Blocks in Gutenberg you can compare it to a component in Vue/React (like `<RichText>` for example._

_block.json_
```json
// voorbeeld toevoegen
```

- `icon` to set one of the WordPress dash-icons (don't prefix with `dashicons-`)
- `category` is where your block will be categorized in the blocks overview
- `parent` the parent block in which this component can be used
- `attributes` are properties (like in Vue) of your block
- `supports` are WordPress features for your block
- `keywords` help your users when they're searching for a block

## Blocks
Blocks are components that can be used in the WordPress editor.

_edit.js_
```js
import './editor.scss';

export default function edit( {} ) {
	return (
		<div></div>	
	);
}
```

### Template
Templates are used to incorporate other (allowed) blocks inside that block. You need to use the `InnerBlocks` component to pass a `template={}` and to set the `allowedBlocks={}`.

_edit.js_
```js
import { InnerBlocks } from '@wordpress/block-editor';

export default function edit( {} ) {
	const _TEMPLATE = [
		[
			'core/heading',
			{},
			[]
		]
	]

	return (
		<div className="td-product-row">  
		   <InnerBlocks  
		      template={ _TEMPLATE }  
		      allowedBlocks={ [ 'core/heading' ] }  
		   />  
		</div>
	);
}
```

### Index.js
Usually you don't need to change anything here, expect when using `InnerBlocks` or when you when you want to set a custom icon rather then the WordPress dash-icons.

_index.js by default_
```js
import { registerBlockType } from '@wordpress/blocks';  
import './style.scss';  
import edit from './edit';  
import metadata from './block.json';  
  
const { name } = metadata;  
  
registerBlockType( name, {  
   ...metadata,  
   edit,  
   save: () => null,  
} );
```

_index.js with InnerBlocks and a custom icon_
```js
import { registerBlockType } from '@wordpress/blocks';  
import { InnerBlocks } from '@wordpress/block-editor';
import './style.scss';  
import edit from './edit';  
import metadata from './block.json';  
import { ReactComponent as Icon } from '../assets/block-icons/icon.svg'
  
const { name } = metadata;  
  
registerBlockType( name, {  
   ...metadata,  
	icon,
   edit,  
   save: () => <InnerBlocks.Content />,  
} );
```
