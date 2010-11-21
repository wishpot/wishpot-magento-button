This plugin allows you to add an "Add to Wishpot" button to Magento.

To install:

 1. Copy the wishpot.phml file to your /frontend/base/default/template/catalog/product/view folder
 2. Add the following line to your /frontend/base/default/layout/catalog.xml file:
        <block type="catalog/product_view" name="product.info.wishpot" as="wishpot" template="catalog/product/view/wishpot.phtml" />
 3. Edit /frontend/base/default/template/catalog/product/view.phtml

In this file, add:
    <?php echo $this->getChildHtml('wishpot') ?>

After every occurence of
    <?php echo $this->getChildHtml('addto') ?>

This probably only occurs twice in this file.  ex.

           <?php if (!$this->hasOptions()):?>
                <div class="add-to-box">
                    <?php if($_product->isSaleable()): ?>
                        <?php echo $this->getChildHtml('addtocart') ?>
                        <?php if( $this->helper('wishlist')->isAllow() || $_compareUrl=$this->helper('catalog/product_compare')->getAddUrl($_product)): ?>
                            <span class="or"><?php echo $this->__('OR') ?></span>
                        <?php endif; ?>
                    <?php endif; ?>
                    <?php echo $this->getChildHtml('addto') ?>
					<?php echo $this->getChildHtml('wishpot') ?>
                </div>
                <?php echo $this->getChildHtml('extra_buttons') ?>
            <?php else:?>
                <?php echo $this->getChildHtml('addto') ?>
				<?php echo $this->getChildHtml('wishpot') ?>
            <?php endif; ?>
