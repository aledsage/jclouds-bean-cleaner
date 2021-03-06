JSON Serializable Example
--------------------------

To generate JSON with serialization (Named) annotations as well as the deserialization annotations generated for the JSON format,
specify 'json_serializable' as the format to the cleaner.

A class can be written short-hand, with @Named and @Nullable annotations, plus field comments as follows::

    package org.jclouds.cleanup.simpletest;
    
    import com.google.inject.name.Named;
    import org.jclouds.javax.annotation.Nullable;
    
    /**
     * Class comment for GrandParent!
     * A few lines....
     * Long
     */
    public class GrandParent {
    
        /** @return name is required */
        @Nullable
        String name;
    
        /** @return attribute is not null */
        String id;
    
        /** @return this is nullable */
        @Nullable
        String description;
        
        @Named("Freddy")
        String freddy;
    
        /** This element is NOT required
         * @return the value of brian
         */    
        @Named("Brian")
        @Nullable
        String[] brian;
    }

This can be converted to a full bean with accessors, to which the field comments will be added, a Builder, etc::

    /*
     * Licensed to jclouds, Inc. (jclouds) under one or more
     * contributor license agreements.  See the NOTICE file
     * distributed with this work for additional information
     * regarding copyright ownership.  jclouds licenses this file
     * to you under the Apache License, Version 2.0 (the
     * "License"); you may not use this file except in compliance
     * with the License.  You may obtain a copy of the License at
     *
     *   http://www.apache.org/licenses/LICENSE-2.0
     *
     * Unless required by applicable law or agreed to in writing,
     * software distributed under the License is distributed on an
     * "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
     * KIND, either express or implied.  See the License for the
     * specific language governing permissions and limitations
     * under the License.
     */
    package org.jclouds.cleanup.simpletest;
    
    import static com.google.common.base.Preconditions.checkNotNull;
    
    import java.beans.ConstructorProperties;
    
    import javax.inject.Named;
    
    import org.jclouds.javax.annotation.Nullable;
    
    import com.google.common.collect.ImmutableMultimap;
    import com.google.common.collect.ImmutableList;
    import com.google.common.collect.ImmutableMap;
    import com.google.common.collect.Sets;
    import com.google.common.collect.ImmutableSet;
    import com.google.inject.name.Named;
    import com.google.common.base.Objects;
    import com.google.common.base.Objects.ToStringHelper;
    
    /**
     * Class comment for GrandParent!
     * A few lines....
     * Long
    */
    public class GrandParent {
    
       public static Builder<?> builder() { 
          return new ConcreteBuilder();
       }
       
       public Builder<?> toBuilder() { 
          return new ConcreteBuilder().fromGrandParent(this);
       }
    
       public static abstract class Builder<T extends Builder<T>>  {
          protected abstract T self();
    
          protected String name;
          protected String id;
          protected String description;
          protected String freddy;
          protected String[] brian;
       
          /** 
           * @see GrandParent#getName()
           */
          public T name(String name) {
             this.name = name;
             return self();
          }
    
          /** 
           * @see GrandParent#getId()
           */
          public T id(String id) {
             this.id = id;
             return self();
          }
    
          /** 
           * @see GrandParent#getDescription()
           */
          public T description(String description) {
             this.description = description;
             return self();
          }
    
          /** 
           * @see GrandParent#getFreddy()
           */
          public T freddy(String freddy) {
             this.freddy = freddy;
             return self();
          }
    
          /** 
           * @see GrandParent#getBrian()
           */
          public T brian(String[] brian) {
             this.brian = brian;
             return self();
          }
    
          public GrandParent build() {
             return new GrandParent(name, id, description, freddy, brian);
          }
          
          public T fromGrandParent(GrandParent in) {
             return this
                      .name(in.getName())
                      .id(in.getId())
                      .description(in.getDescription())
                      .freddy(in.getFreddy())
                      .brian(in.getBrian());
          }
       }
    
       private static class ConcreteBuilder extends Builder<ConcreteBuilder> {
          @Override
          protected ConcreteBuilder self() {
             return this;
          }
       }
    
       private final String name;
       private final String id;
       private final String description;
       @Named("Freddy")
       private final String freddy;
       @Named("Brian")
       private final String[] brian;
    
       @ConstructorProperties({
          "name", "id", "description", "Freddy", "Brian"
       })
       protected GrandParent(@Nullable String name, String id, @Nullable String description, String freddy, @Nullable String[] brian) {
          this.name = name;
          this.id = checkNotNull(id, "id");
          this.description = description;
          this.freddy = checkNotNull(freddy, "freddy");
          this.brian = brian;
       }
    
       /**
        * @return name is required
        */
       @Nullable
       public String getName() {
          return this.name;
       }
    
       /**
        * @return attribute is not null
        */
       public String getId() {
          return this.id;
       }
    
       /**
        * @return this is nullable
        */
       @Nullable
       public String getDescription() {
          return this.description;
       }
    
       public String getFreddy() {
          return this.freddy;
       }
    
       /**
        * This element is NOT required
        * 
        * @return the value of brian
        */
       @Nullable
       public String[] getBrian() {
          return this.brian;
       }
    
       @Override
       public int hashCode() {
          return Objects.hashCode(name, id, description, freddy, brian);
       }
    
       @Override
       public boolean equals(Object obj) {
          if (this == obj) return true;
          if (obj == null || getClass() != obj.getClass()) return false;
          GrandParent that = GrandParent.class.cast(obj);
          return Objects.equal(this.name, that.name)
                   && Objects.equal(this.id, that.id)
                   && Objects.equal(this.description, that.description)
                   && Objects.equal(this.freddy, that.freddy)
                   && Objects.equal(this.brian, that.brian);
       }
       
       protected ToStringHelper string() {
          return Objects.toStringHelper(this)
                .add("name", name).add("id", id).add("description", description).add("freddy", freddy).add("brian", brian);
       }
       
       @Override
       public String toString() {
          return string().toString();
       }
    
    }
